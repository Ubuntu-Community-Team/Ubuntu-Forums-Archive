---
title: "Kernel update"
date: 2014-04-11
forum: Installation &amp; Upgrades
---

### Post by gopukrishnan on 2014-04-11
Hi all,

I want to configure DRBD in my Rackspace cloud servers. While following the  online guides, I can see that the kernel should be updated that support  drbd. When I check in the servers, I can see drbd module is not  included in my server kernel.

```
root@test1:~# modprobe drbd
FATAL: Module drbd not found.
```


I have tried to update the kernel module by apt-get upgrade but it is showing upto date.

 ```
root@test1:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-virtual
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

 kindly advise....

Gopu

---

### Post by Kirboosy on 2014-04-11
The package is being heldback. The following command will tell apt-get to update it.

```
sudo apt-get dist-upgrade
```

So what's the difference between upgrade and dist-upgrade?

> upgrade -- upgrade is used to install the newest versions of all packages currently installed on the system
> dist-upgrade -- in addition to performing the function of upgrade, also  intelligently handles changing dependencies with new versions of  packages

Hope that helps!
~Caboose

---

### Post by Double.J on 2014-04-11
Hi there!


The documentation states that DRBD is compiled into the server kernel by default.


The exception is that DRBD is not compiled into the virtual server kernel. And must be done so by the user. Updating will not resolve if it is the virtual machine kernel. The documentation recommends installing the linux-server package. 


More info
[10.04]("https://help.ubuntu.com/10.04/serverguide/drbd.html")
[12.04]("https://help.ubuntu.com/12.04/serverguide/drbd.html")


Hope it's helpful, 


Jj

---

