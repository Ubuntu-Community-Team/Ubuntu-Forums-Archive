---
title: "Problems using &quot;apt-get&quot; Configuration keeps reseting."
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by tigerplug on 2007-08-02
Im using Ubuntu on a network that has a proxy. I'm able to connect to the internet fine but I can't run updates or use the terminal to issue commands like "apt-get"

I've taken a screenshot of the terminal and highlighted where I think the problem is. When I type "sudo apt-get update" I see the following screen:
[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Ubuntu/Screenshot-shaneshane-desktop.png[/IMG]

You can see that the IP address that Ubuntu is trying to use as the proxy is highlighted. 
**THIS IS NOT THE IP ADDRESS OF THE PROXY**

Is there anyway that I can change this so that it points to the right IP?

---

### Post by dougfractal on 2007-08-02
you have to set environmental variable
under bash

export http_proxy='proxy.domain: port'

e.g.
export http_proxy="192.125.196.3:8080"

---

### Post by tigerplug on 2007-08-02
> **dougfractal said:**
> you have to set environmental variable
under bash

export http_proxy='proxy.domain: port'

e.g.
export http_proxy="192.125.196.3:8080"


Thanks, do I need to include my Proxy Password or Username?

---

### Post by tigerplug on 2007-08-02
> **dougfractal said:**
> you have to set environmental variable
under bash

export http_proxy='proxy.domain: port'

e.g.
export http_proxy="192.125.196.3:8080"

No, doesn't seem to work.

I've entered the following command ino the terminal to configure my proxy:
```
export http_proxy="194.125.196.3:8080"
```

After entering this I get no response. Terminal brings me down a line.

I then type ```
sudo apt-get update
``` , press return and I get this screen:
[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Ubuntu/terminal2.png[/IMG]

Is there anywhere else that I should be using this code?

---

### Post by dougfractal on 2007-08-02
from [http://ubuntuforums.org/showthread.php?t=1575](http://ubuntuforums.org/showthread.php?t=1575)

> export http_proxy="http://username: password@host: port/"  (no spaces by the : 's -- they keep going to icons)

---

### Post by tigerplug on 2007-08-02
> **dougfractal said:**
> from [http://ubuntuforums.org/showthread.php?t=1575](http://ubuntuforums.org/showthread.php?t=1575)

  (no spaces by the : 's -- they keep going to icons)


Thanks for that, it seems to work. 
I am getting an error but not in relation to the proxy when I " sudo apt-get update"

---

### Post by dougfractal on 2007-08-02
so what happens when you 
```
ping -c 4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com)
```

should be ping -c 4 [ie.archive.ubuntu.com](ie.archive.ubuntu.com)[/CODE]

---

### Post by tigerplug on 2007-08-02
> **dougfractal said:**
> so what happens when you 
```
ping -c 4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com)
```



I get :

```

shane@shane-desktop:~$ ping -c 4 http://ie.archive.ubuntu.com
ping: unknown host http://ie.archive.ubuntu.com
shane@shane-desktop:~$ 
```


This cant be right?

---

### Post by dougfractal on 2007-08-02
so what happens when you (should have been) ```
wget ie.archive.ubuntu.com
```

It looks like you proxy settings aren't working

echo $http_proxy


unset http_proxy
export http_proxy="http://username:password@host:port/"


Notes:  (Things i've just found out)
ping doesn't use proxy
so use wget instead.
ping -c 4 ie.archive.ubuntu.com    # no http://

---

### Post by tigerplug on 2007-08-02
> **dougfractal said:**
> so what happens when you (should have been) ```
wget ie.archive.ubuntu.com
```

It looks like you proxy settings aren't working

echo $http_proxy


unset http_proxy
export http_proxy="http://username:password@host:port/"


Notes:  (Things i've just found out)
ping doesn't use proxy
so use wget instead.
ping -c 4 ie.archive.ubuntu.com    # no http://

wget ie.archive.ubuntu.com gives me :
```
shane@shane-desktop:~$ wget ie.archive.ubuntu.com
--16:59:15--  http://ie.archive.ubuntu.com/
           => `index.html'
Connecting to 192.125.196.3:8080... failed: Connection refused.
shane@shane-desktop:~$ 
```

Then:
```
shane@shane-desktop:~$ echo $http_proxy
http://useer:password@proxyip:8080
shane@shane-desktop:~
```$ 

I was able to ping Google by saying:
```

ping www.google.com

```

---

### Post by dougfractal on 2007-08-02
> **tigerplug said:**
> wget ie.archive.ubuntu.com gives me :
```
shane@shane-desktop:~$ wget ie.archive.ubuntu.com
--16:59:15--  http://ie.archive.ubuntu.com/
           => `index.html'
Connecting to 192.125.196.3:8080... failed: Connection refused.
shane@shane-desktop:~$ 
```

Then:
```
shane@shane-desktop:~$ echo $http_proxy
http://useer:password@proxyip:8080
shane@shane-desktop:~
```$ 


> **tigerplug said:**
> 
You can see that the IP address that Ubuntu is trying to use as the proxy is highlighted. 
**THIS IS NOT THE IP ADDRESS OF THE PROXY**

Is there anyway that I can change this so that it points to the right IP?

I'm confused in your top post Proxy is not 192.125.196.3:8080  you've exported the new proxy values: 
export http_proxy="user:password@proxyip:8080"

but you still get "Connecting to 192.125.196.3:8080... failed: Connection refused." with wget

---

### Post by tigerplug on 2007-08-20
Yup! I'm puzzled on this one. Its a shame really.

---

### Post by dougfractal on 2007-08-23
from [http://ubuntuforums.org/showthread.php?t=96802](http://ubuntuforums.org/showthread.php?t=96802)

gedit /etc/apt/apt.conf
> Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT";

---

