---
title: "apt-get dist-upgrade crash cleanup"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by gopher2x on 2008-07-05
I did a apt-get dist-upgrade but the kernel install fails because of low disk space. So i am trying to undo the dist-upgrade but unable to.
so im stuck here

root@radio:/boot# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 15.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 22469 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@radio:/boot# 





what do you guys think? how can i fix this??

---

### Post by Partyboi2 on 2008-07-05
deleted

---

### Post by jw5801 on 2008-07-05
> **gopher2x said:**
> I did a apt-get dist-upgrade but the kernel install fails because of low disk space. So i am trying to undo the dist-upgrade but unable to.
so im stuck here

root@radio:/boot# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 15.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 22469 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@radio:/boot# 





what do you guys think? how can i fix this??

Well, if you know you have no space left, upgrading packages is probably a bad idea! Or is it just on your boot partition that you have no space? Either way, my suggestion would be to remove the older kernels to free up some space:
```
sudo apt-get remove linux-image-2.6.24-16-generic linux-image-2.6.24-17-generic
```

That is of course assuming that you are currently booted into the 2.6.24-18 kernel. If you're still using 2.6.24-17, don't remove it. If you're jumping straight from 2.6.24-16 to 2.6.24-19, we'll have to look at some other way of getting some free space to play with.

---

### Post by VMC on 2008-07-05
Output disk free from a Terminal:

```
df
```

---

### Post by jw5801 on 2008-07-05
> **VMC said:**
> Output disk free from a Terminal:

```
df
```

```
df -h
```is easier to read :)

---

