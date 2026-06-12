---
title: "[SOLVED] E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by pstorch on 2007-09-03
Hi,

I've installed Ubuntu 7.04 from the Desktop CD. 
First a got a Kernel Panic after the first boot. I solved it by adding an initrd entry into the /boot/grub/menu.lst.
Second I had to manually install ndiswrapper to get a internet connection via my Wifi card.

Since then I can use Ubuntu. I have been able to install some more packages and I get the automatic update notifications.

However: after the first Kernel updates I constantly run into a post installation error:

```
peter@bigbrother:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
/bin/sh: Can't open getopt
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.20-16-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I know it's not good manner to post questions into different forums in parallel, but maybe someone can help me in the international Ubuntu Forum.

I originally asked this question in the german forum: [http://forum.ubuntuusers.de/topic/112325/]("http://forum.ubuntuusers.de/topic/112325/")

No solution so far. If it will be solved in the german forum I'll post the solution here, too.

regards,
Peter

---

### Post by ThrobbingBrain66 on 2007-09-03
Try
```
sudo dpkg --configure -a
```

---

### Post by pstorch on 2007-09-04
Hi,

sudo dpkg --configure -a:

```
peter@bigbrother:~$ sudo dpkg --configure -a
Password:
Setting up initramfs-tools (0.85eubuntu10) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic.bak
/bin/sh: Can't open getopt
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.20-15-generic.bak
dpkg: error processing initramfs-tools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-2.6.20-16-generic:
 linux-image-2.6.20-16-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 linux-image-2.6.20-16-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

```

---

### Post by Monosabio on 2007-09-04
Same error:

```

User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.20-16-lowlatency
 linux-image-2.6.20-16-generic

```

---

### Post by pstorch on 2007-09-07
Hi,

this problem has been solved.

The root cause was this error:
```
/bin/sh: Can't open getopt
```

You can find it at the very top of the first post.

The **/usr/bin/getopt** executable was corrupt somehow. You can verify it with:

```
peter@bigbrother:~$ file /usr/bin/getopt
/usr/bin/getopt: data 
```

After **aptitude reinstall util-linux** it was corrected and the same command looks like this now:

```
/usr/bin/getopt: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped 
```

After this fix the Kernel updated succeeded.

See details in the german thread.

---

### Post by oderus on 2007-10-02
Thank you !!!!

I had the same problem when I performed an upgrade from Gutsy Alpha 5 to whatever was released Oct 1rst.

---

