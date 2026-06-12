---
title: "Ubuntu 13.10 dropping WiFi connection"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by johwilsmi on 2013-12-31
Fairly new to Linux and new to Ubuntu. Bought new cheap computer to install and run Linux distributions on (had a text only Linpus distro already installed). Installed Ubuntu 13.10 on computer and it would not stay connected to my WiFi. Installed it twice just to see that I did the install correctly. This connection has worked for years with my Mac, Windows 7 and Windows 8.1 computers.
Installed Ubuntu 12.04 and the computer stays connected and works perfectly.  IS THIS A BUG IN 13.10 RELEASE ?
I re-installed 13.10 next to my 12.04 release and at this point am NOT having WiFi disconnect problems. I am beginning to believe that I did something wrong on the previous 2 installs of 13.10 but I do not know what I did wrong. I will leave this post in place for a while in case the problem returns so that everyone can know it is a problem.

---

### Post by varunendra on 2014-01-04
Welcome to the forums johwilsmi !

If the problem returns, be sure to post the update in a new post, otherwise the thread won't come up in regular search results or forum listing and nobody would know there is an update.

Also, it may be helpful to us as a kind feedback if you can show us the card you are using and the version of kernel and driver for it. This can be listed by the following commands -
```
uname -mr
lspci -nnk | grep -iA2 net
nm-tool
```

If it happens to be a USB card (some internal cards can also be internally connected via USB), then also the output of -
```
lsusb
```

Hope the updates have fixed it permanently and you won't face any problems with it again. :)

---

