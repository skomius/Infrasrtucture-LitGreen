# Infrasrtucture-LitGreen
  Infrastructure for LitGreen app providing kubernetes cluster, jenkins server, logging infrastructure.
## Requirements
  Windows 10=<, Hyper-V, 16 gb ram
## Setup
### 1. Minikube installation 
1. Open powershell in administrator mode
2. Enable hyper-v: 
   ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
   ```
3. Download and install minikube:
   ```powershell
    New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
    Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri 'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing
   ```
4. Add the minikube.exe binary to your PATH:
   ```powershell
    $oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
    if ($oldPath.Split(';') -inotcontains 'C:\minikube'){
    [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
    }
   ```
5. Configuration at $home\\.kube (optional)
       
### 2. Start minikube cluster
1. Starts hyper-v virtual machine with minikube kubernetes cluster:
    ```powershell
     minikube start --driver=hyperv 
    ```
### 2. Add Jenkins server

    
## Uninstall
### Uninstall minikube cluster
1. Remove minikube hyper-v virtual machine:
  ```powershell
   minikube delete 
  ```
2. Delete directory "c:\minikube"
