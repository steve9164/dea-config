# Do stuff with k8s
get-pods:
	kubectl get pods  --namespace=alchemist-processor
add-to-queue:
	kubectl create -f wofs-addqueue.yaml

kill-queue:
	kubectl delete -f wofs-addqueue.yaml

redo-queue:
	make kill-queue
	make add-to-queue

deploy-workers:
	kubectl create -f wofs-processqueue.yaml

update-workers:
	kubectl replace -f wofs-processqueue.yaml

undeploy-workers:
	kubectl delete -f wofs-processqueue.yaml

logs:
	kubectl --namespace=alchemist-processor logs -f $(pod)

deploy-dev:
	kubectl create -f dev-box.yaml

undeploy-dev:
	kubectl delete -f dev-box.yaml

restart-dev:
	make undeploy-dev
	make deploy-dev

cmd:
	kubectl exec -it dev-box /bin/bash --namespace=alchemist-processor
