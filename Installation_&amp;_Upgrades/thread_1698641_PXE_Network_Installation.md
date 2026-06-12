---
title: "PXE Network Installation"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by furex on 2011-03-02
Hi everybody,

I am trying to install Ubuntu 10.10 on a old notebook booting from PXE (it is the only way I have).

I am following this article:
[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

I succesfully booted in PXE and loaded the installation kernel.

I am using the KS functionality using ks.cfg script as follow:

```

## on the pxelinux.cfg/default
append ks=http://192.168.1.1/ks.cfg .....

##the ks.cg is
install
url --url http://192.168.1.1/ubuntu


```


192.168.1.1 is my DHCP server and TFTBOOT Server (it's another ubuntu 10.10)

I have mounted on /var/www/ubuntu/ the ISO of Ubuntu 10.10.

When I run firefox browsing  192.168.1.1 i can reach booth the ks.cfg and the 192.168.1.1/ubuntu path and see all the stuff inside.

The problem is that during the installation I got an error saying that is impossible to download the installation files from the mirror.

Any suggestion will be really appreciated!

Enrico

---

