---
title: "Configure error on updating kernel to 2.6.30-9"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2009-06-13
Updating from karmic repositories yesterday, I received the following message from synaptic:

```
E: linux-image-2.6.30-9-generic: subprocess post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured
```

Trying to correct it, I get the terminal output:
```
yotam@ubuntu:~$ sudo apt-get install -f
[sudo] password for yotam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.30-9-generic (2.6.30-9.10) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-9-generic
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.30-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.30-9-generic; however:
  Package linux-image-2.6.30-9-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.30.9.8); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.30-9-generic
 linux-image-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The new kernel, of course, is not bootable. Did this happen to anyone else? How can it be solved?

---

### Post by jppr on 2009-06-13
[LIST=1]
[*]sudo aptitude update 
[*]sudo aptitude -f install 
[*]sudo dpkg --configure -a 
[*]sudo aptitude dist-upgrade
[/LIST]
try update that way or do it synaptic. i update my system always synaptic.

---

### Post by psyke83 on 2009-06-13
> **Wise Ferret said:**
> Updating from karmic repositories yesterday, I received the following message from synaptic:

```
E: linux-image-2.6.30-9-generic: subprocess post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured
```

Trying to correct it, I get the terminal output:
```
yotam@ubuntu:~$ sudo apt-get install -f
[sudo] password for yotam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.30-9-generic (2.6.30-9.10) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-9-generic
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.30-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.30-9-generic; however:
  Package linux-image-2.6.30-9-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.30.9.8); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.30-9-generic
 linux-image-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The new kernel, of course, is not bootable. Did this happen to anyone else? How can it be solved?

```
$ sudo ln -s /usr/sbin/update-grub /sbin/update-grub
$ sudo apt-get install -f
$ sudo apt-get dist-upgrade
```

---

### Post by Wise Ferret on 2009-06-13
Thank you very much - the grub tip worked!
I guess that the kernel configuration scripts are not yet fully grub2-aware.

---

### Post by xebian on 2009-06-13
> **Wise Ferret said:**
> Thank you very much - the grub tip worked!
I guess that the kernel configuration scripts are not yet fully grub2-aware.

Your problem is because the meta package linux-image has not been updated
```
 linux-image depends on linux-image-generic (= 2.6.30.9.8); however:

```

You can get rid of it to resolve the issue and future issue

---

