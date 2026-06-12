---
title: "VPN connection after minimal install"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by joe84maiden on 2007-06-06
I have had serious problems connecting to my only form of internet connection (VPN) after the text based Xubuntu install. I had a variety of programs which I wanted to install/download on top of this base system for the system to have any purpose at all. Unfortunately when I tried to connect to the internet there is seemingly no way of connecting via VPN in the base install. This made things very difficult, as the network-manager has many dependencies that are unfulfilled in the base package. The only way I could find of doing this was to make another computer become a repository mirror for universe and multiverse and then download all of the repositories on to an external hard drive. I then mounted the drive on the non-networked computer and added the folders as repositories and installed from there. Is there an easy way of doing this for the next install???

Thanks

---

### Post by arkham on 2007-06-07
Rather than mirroring everything on one machine you could install squid on it and use that to proxy the requests outward to the internet during the install, then shut down the proxy server once you are done if worried about leaving it running.  If that sounds like an option, then just do some googling for squid configs or read the man pages - I have done this in the past and it really is not terribly difficult.

Once you have the proxy up and running, specifying it for apt is quite easy.  If it was on 192.168.1.1 port 8080 for example you would run:
```

export http_proxy="http://192.168.1.1:8080"
sudo apt-get update
sudo apt-get install <package name>
```

---

