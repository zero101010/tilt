# local_resource(
#     'simple-api-compile',
#     cmd='CGO_ENABLED=0 G00S=linux GOARCH=arm64 go build -o build/simple-api main.go',
#     deps = ['main.go', 'go.mod','go.sum'],
#     labels = ['simple-api-compile']
# )
## Precisa dizer onde vai ser usado, pois se não usar 


docker_build(
    'zero101010/simple-api-go',
    ".",
    dockerfile='dockerfiles/Dockerfile',
    # Atualiza o container de acordo com as mudanças sem precisar rebuildar as imagens
    # live_update=[
    #     sync(local_path='./build',remote_path='/app )
    # ],
)

k8s_yaml([
    'k8s/deployment.yaml',
    'k8s/service.yaml'
])

k8s_resource(
    'simple-api-go',
    port_forwards='8080:8080',
    labels='simple-api-go'
)


