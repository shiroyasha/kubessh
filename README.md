# KubeSSH

Simple way to jump into your pods.

Note: Technically, we are not running SSH, but the usage pattern is similar.

## Installation

``` bash
sudo git clone https://github.com/shiroyasha/kubessh.git /opt/kubessh
sudo ln -s /opt/kubessh/kubessh /usr/local/bin/kubessh
```

## Usage

List available pods:

``` bash
$ kubessh
NAME                    READY     STATUS    RESTARTS   AGE
app-2944817255-t7852    1/1       Running   0          1d
nginx-2865216395-nlphp  1/1       Running   0          1d
```

Enter a pod:

``` bash
$ kubessh nginx
** running: kubectl exec -ti nginx-2865216395-nlphp -- /bin/bash **
root@nginx-2865216395-nlphp $
```

Execute an arbitrary command on the pod:

``` bash
$ kubessh app cat app.rb
** running: kubectl exec -ti nginx-2865216395-nlphp -- cat app.rb **
require "sinatra"

get "/" do
  "Hello World"
end
```

``` bash
$ kubessh nginx top
** running: kubectl exec -ti nginx-2865216395-nlphp -- top **
```
