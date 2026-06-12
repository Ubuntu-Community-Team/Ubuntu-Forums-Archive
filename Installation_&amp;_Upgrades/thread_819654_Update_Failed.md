---
title: "Update Failed"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-06-05
When trying to update via synaptic, I got a message saying 3 updates had failed. Trying again to run it on the command line, I get:
```

bbraun@bbraun-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-ubuntu-modules-2.6.24-18-generic (2.6.24-18.26) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any fix?

---

### Post by viljun on 2008-06-05
> **JustAnotherVagueAnon said:**
> gzip: stdout: No space left on device

Do you have enough space on your partition? Open terminal and type 'free -h' to see space available.

I'm not sure but you maybe should update first and upgrade after updating. Updating goes like this 'sudo apt-get update'

---

### Post by avtolle on 2008-06-05
You need to create some space on the partition, which, unless you have a separate /Boot partition, will be the / partition.

---

### Post by JustAnotherVagueAnon on 2008-06-05
```

bbraun@bbraun-desktop:~$ free h
             total       used       free     shared    buffers     cached
Mem:       2054920     967520    1087400          0      18912     365568
-/+ buffers/cache:     583040    1471880
Swap:      1992020          0    1992020

```
It appears I have free space... Now what?

---

### Post by abn91c on 2008-06-05
dpkg --configure -a,then sudo apt-get install -f

---

### Post by JustAnotherVagueAnon on 2008-06-05
Same thing...
```

bbraun@bbraun-desktop:~$ sudo dpkg --configure -a
Setting up linux-ubuntu-modules-2.6.24-18-generic (2.6.24-18.26) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-generic

```
I'm not sure how I should free up space... This problem is started to affect other things as well...

EDIT:
> **avtolle said:**
> You need to create some space on the partition, which, unless you have a separate /Boot partition, will be the / partition.
You were correct. BOOT is 100% full, but I'm still not sure how to fix it. Can I link partitions somehow or add space or delete anything?

---

### Post by JustAnotherVagueAnon on 2008-06-06
Deleted an old kernel to free up space... I should've done that in the first place heh. Works now.

---

### Post by zvacet on 2008-06-06
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by iaculallad on 2008-06-06
```
sudo apt-get install util-linux
sudo apt-get update && sudo apt-get upgrade
```

---

