---
title: "Search for packages in terminal"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by h66m9d on 2012-09-21
hi!:D
How can I search between packages that can be install from internet in terminal with prefix?
Sample: I want to install a software but I don't know full name of that.
For example I need search "proxyf" for "proxychains"
Can I search for that in terminal?

---

### Post by nothingspecial on 2012-09-21
You would use apt-cache search. The -n option searches names only and supports regex so you can use a ^ to anchor proxy to the beginning or a $ to anchor chains to the end etc

```
apt-cache search -n ^proxy
proxychains - proxy chains - redirect connections through proxy servers
proxycheck - checks existence of open proxy
proxytrack - Build HTTP Caches using archived websites copied by HTTrack
proxytunnel - Create tcp tunnels trough HTTPS proxies, for using with SSH


```

```
apt-cache search -n chains$
proxychains - proxy chains - redirect connections through proxy servers
```

---

### Post by h66m9d on 2012-09-21
> **nothingspecial said:**
> You would use apt-cache search. The -n option searches names only and supports regex so you can use a ^ to anchor proxy to the beginning or a $ to anchor chains to the end etc

```
apt-cache search -n ^proxy
proxychains - proxy chains - redirect connections through proxy servers
proxycheck - checks existence of open proxy
proxytrack - Build HTTP Caches using archived websites copied by HTTrack
proxytunnel - Create tcp tunnels trough HTTPS proxies, for using with SSH


```

```
apt-cache search -n chains$
proxychains - proxy chains - redirect connections through proxy servers
```
Thanks a lot :D

---

### Post by h66m9d on 2012-09-21
And how can I search between my installed software in terminal?

---

### Post by codemaniac on 2012-09-21
> **h66m9d said:**
> And how can I search between my installed software in terminal?

Use dpkg -l , if a package(say git) is installed the below commandline would return you the details .

```
dpkg -l | awk '$1 ~ /^ii/ && $2 ~ /git/{print}'
```

---

### Post by nothingspecial on 2012-09-21
```
dpkg --get-selections | grep regex
```


For example if you know it starts with "app" 

```
dpkg --get-selections | grep ^app
app-install-data				install
app-install-data-partner			install
apparmor					install
appmenu-gtk					install
appmenu-gtk3					install
appmenu-qt					install
apport						install
apport-gtk					install
apport-symptoms					install

```

---

### Post by h66m9d on 2012-09-21
it work.
Thank you!

---

