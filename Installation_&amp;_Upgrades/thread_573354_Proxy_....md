---
title: "Proxy ..."
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by wwoollff on 2007-10-11
Hi. I'm in a collage campus, where every student is allowed to use the internet only throw a local proxy.The problem is that the proxy allows transfer only throw the ports for HTTP, FTP, SSH and MAIL....and maybe some more.So I cannot download  torrents and stuff like that...but this is not the problem.The problem is that I'm trying to upgrade my Kubuntu Gutsy, but the apt-get isn't working...and also Kopete and other programs.Is there a way to upgrade throw the 8080 port? or maybe this is not the problem ...
thx

---

### Post by Shootfast on 2007-10-12
You will have to place your proxy settings into the KDE control center under the proxy tab. This setting is global for KDE applications. Failing that, you can also try changing the environmental variables in the terminal with 

```
export HTTP_PROXY='your.proxy.address:PORT'
```

---

