---
title: "synaptic broken?"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by gopher2x on 2008-01-04
trying to start synaptic i get the error message 
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

```

however

when i run the command it does not work
```
david@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for david:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1


```

any ideas what i should do?

---

### Post by Sef on 2008-01-05
Go into GRUB and change to a different kernel.  Once you do that, see if you have the same problem or not.

To get into GRUB, press esc at the start of the boot process, you will have about 3 seconds to do it.

---

### Post by gopher2x on 2008-01-05
same problem any other ideas? i dont want to reinstall again

---

### Post by gopher2x on 2008-01-05
anyone any ideas? I dont want to install....

---

### Post by Partyboi2 on 2008-01-05
What is the output to this command
```
getopt -V
```

---

### Post by Athe1st on 2008-02-13
as I see command
**sudo dpkg -C**
may show two unfinished packages:
* initramfs-tools
* linux-image-2.6.22-14-generic

the first one is broken, the second - not installed

In my case (the same problem) I found out an issue:
[B]sudo dpkg-reconfigure -a
sudo apt-get upgrade[/B]

Now no broken packages and Synaptic is started :)

---

