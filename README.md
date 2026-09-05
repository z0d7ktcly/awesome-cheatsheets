#!/bin/bash
# Kubernetes Cheatsheet

### PODS ###
kubectl get pods                        # List all pods in the current namespace
kubectl get pods -o wide                # List all pods with node and IP info
kubectl get pods --all-namespaces       # List all pods across all namespaces
kubectl describe pod <pod-name>         # Show detailed state of a pod
kubectl delete pod <pod-name>           # Delete a pod
kubectl logs <pod-name>                 # Print logs for a pod
kubectl logs -f <pod-name>              # Stream logs for a pod
kubectl exec -it <pod-name> -- /bin/sh  # Execute interactive shell in a pod

### OBSERVABILITY & TROUBLESHOOTING ###
kubectl top node                        # Show node CPU and memory usage
kubectl top pod                         # Show pod CPU and memory usage
kubectl debug pod/<pod-name> -it --image=busybox # Attach ephemeral debug container
kubectl get events --sort-by='.metadata.creationTimestamp' # Sort cluster events by time

### DEPLOYMENTS & SERVICES ###
kubectl get deployments                 # List all deployments
kubectl rollout status deployment/<name> # Check rollout status
kubectl rollout restart deployment/<name># Restart a deployment
kubectl get svc                         # List all services
kubectl port-forward svc/<name> 8080:80 # Port forward service to localhost

### CONFIG & CONTEXT ###
kubectl config get-contexts             # Display list of contexts
kubectl config use-context <context>    # Switch current context
kubectl config set-context --current --namespace=<ns> # Set default namespace