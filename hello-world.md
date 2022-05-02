# hello-world

## overview

k8sをつかってコンテナを動かしてみる。

## とりあえず動かしてみる

デプロイ

``` powershell
> kubectl run hello-world --image hello-world --restart=Never
pod/hello-world created
```

状況確認

``` powershell
# podの確認
> kubectl get pod
NAME          READY   STATUS              RESTARTS   AGE
hello-world   0/1     ContainerCreating   0          11s

# ログ確認
> kubectl logs pod/hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

# podの削除
> kubectl delete pod/hello-world
pod "hello-world" deleted
```

## マニフェストで動かしてみる

デプロイ

``` powershell
> kubectl apply -f .\hello-world.yml
pod/test created
```

状況確認

``` powershell
# podの確認
> kubectl get -f .\hello-world.yml
NAME   READY   STATUS             RESTARTS     AGE
test   0/1     CrashLoopBackOff   1 (6s ago)   41s

# ログ確認
> kubectl logs test

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

# podの削除
> kubectl delete -f hello-world.yml
pod "test" deleted
```

# 参考資料

* [k8s環境ハンズオン k8s基本学習編](https://qiita.com/gamelike319/items/773aea9ac201becee300)
