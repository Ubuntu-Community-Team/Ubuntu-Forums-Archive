---
title: "Failure tyring to update to Kernel 4.14.37"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2018-04-29
I tried to install kernel 4.14.37 and got:

```
root@Charon:~/Downloads# dpkg -i *.deb
Selecting previously unselected package linux-headers-4.14.37-041437.
(Reading database ... 229084 files and directories currently installed.)
Preparing to unpack linux-headers-4.14.37-041437_4.14.37-041437.201804261030_all.deb ...
Unpacking linux-headers-4.14.37-041437 (4.14.37-041437.201804261030) ...
Selecting previously unselected package linux-headers-4.14.37-041437-generic.
Preparing to unpack linux-headers-4.14.37-041437-generic_4.14.37-041437.201804261030_amd64.deb ...
Unpacking linux-headers-4.14.37-041437-generic (4.14.37-041437.201804261030) ...
Selecting previously unselected package linux-image-unsigned-4.14.37-041437-generic.
Preparing to unpack linux-image-unsigned-4.14.37-041437-generic_4.14.37-041437.201804261030_amd64.deb ...
Unpacking linux-image-unsigned-4.14.37-041437-generic (4.14.37-041437.201804261030) ...
Selecting previously unselected package linux-modules-4.14.37-041437-generic.
Preparing to unpack linux-modules-4.14.37-041437-generic_4.14.37-041437.201804261030_amd64.deb ...
Unpacking linux-modules-4.14.37-041437-generic (4.14.37-041437.201804261030) ...
Setting up linux-headers-4.14.37-041437 (4.14.37-041437.201804261030) ...
Setting up linux-headers-4.14.37-041437-generic (4.14.37-041437.201804261030) ...
Setting up linux-modules-4.14.37-041437-generic (4.14.37-041437.201804261030) ...
Setting up linux-image-unsigned-4.14.37-041437-generic (4.14.37-041437.201804261030) ...
/var/lib/dpkg/info/linux-image-unsigned-4.14.37-041437-generic.postinst: 50: /var/lib/dpkg/info/linux-image-unsigned-4.14.37-041437-generic.postinst: linux-update-symlinks: not found
dpkg: error processing package linux-image-unsigned-4.14.37-041437-generic (--install):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-unsigned-4.14.37-041437-generic
root@Charon:~/Downloads# 


```

What should I do resolve this please?

Grump - it was also very hard to remove these pacakges becasue the prerremove script was also not present :(   

How to apply latest linux-base to 16.04?

I've been *strongly* advised by btrfs team to upgrade to 4.14 kernel or later - I'm currently on 16.04.4LTS so what kernel should I install please if this one won't work.

Thanks
David

---

### Post by Xian on 2018-04-29
[FONT=Roboto]First make sure you have [/FONT]linux-base_4.5ubuntu1_all.deb[FONT=Roboto] installed. [/FONT]
[FONT=Roboto]
[/FONT][https://ubuntu.pkgs.org/16.04/ubuntu-main-amd64/linux-base_4.0ubuntu1_all.deb.html](https://ubuntu.pkgs.org/16.04/ubuntu-main-amd64/linux-base_4.0ubuntu1_all.deb.html)

Next install your linux-modules[FONT=Roboto] package. 

Then try to cleanly install the kernel. [/FONT]

---

### Post by David_Partridge on 2018-04-30
Thanks

David

---

