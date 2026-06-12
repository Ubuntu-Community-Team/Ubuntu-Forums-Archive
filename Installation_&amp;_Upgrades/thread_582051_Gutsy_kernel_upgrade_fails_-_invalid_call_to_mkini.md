---
title: "Gutsy kernel upgrade fails - invalid call to mkinitramfs?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2007-10-19
Hi everyone,

I've run into problems installing linux-image-2.6.22-generic during upgrade. I've attached the report from dpkg which seems to think the kernel deb is trying to run mkinitramfs -c (something) which isn't a valid switch.

```
Selecting previously deselected package linux-image-2.6.22-14-generic.
(Reading database ... 167596 files and directories currently installed.)
Unpacking linux-image-2.6.22-14-generic (from .../linux-image-2.6.22-14-generic_2.6.22-14.46_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.22-14-generic.
Unpacking linux-ubuntu-modules-2.6.22-14-generic (from .../linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_i386.deb) ...
Setting up linux-image-2.6.22-14-generic (2.6.22-14.46) ...
Running depmod.
/usr/sbin/mkinitramfs: invalid option -- c
Terminating...
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.22-14-generic (2.6.22-14.46) ...
Running depmod.
/usr/sbin/mkinitramfs: invalid option -- c
Terminating...
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-ubuntu-modules-2.6.22-14-generic
Press return to continue.

```

I could generate the initramfs myself, but the package manager still complains the package is broken (which it is) when I do anything else. I tried moving mkinitramfs, creating a symlink etc to see if the package was supposed to call update-initramfs but -o was passed which is correct syntax for mkinitramfs.

Does anyone know how on earth I fix this? Is this a bug?

Quark_77

---

### Post by fabian.vogler on 2007-10-20
Same problem here! Didn't find a solution yet ... but others seem also to have problems with the kernel: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/152820](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/152820)

```
$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.22-14-generic (2.6.22-14.46) ...
Running depmod.
/usr/sbin/mkinitramfs: invalid option -- c
Terminating...
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.22-14-generic; however:
  Package linux-ubuntu-modules-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.22-14-generic; however:
  Package linux-restricted-modules-2.6.22-14-generic is not configured yet.
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
 linux-image-2.6.22-14-generic
 linux-ubuntu-modules-2.6.22-14-generic
 linux-image-generic
 linux-restricted-modules-2.6.22-14-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by vouzico on 2007-11-05
I have exactly the same problem on my HP laptop :/

Did someone find a solution ?

---

### Post by Critias on 2007-11-06
I had the same problem, used a quick and dirty hack to solve it:
moved mkinitramfs out of the way:
$ sudo mv /usr/sbin/mkinitramfs /usr/sbin/mkinitramfs.org
and placed my own little script there that called /usr/sbin/mkinitramfs.org with the Right parameters:
$ sudo vim /usr/sbin/mkinitramfs

#!/bin/bash
/usr/sbin/mkinitramfs.org -v -o /boot/initrd.img-2.6.22-14-generic -k 2.6.22-14-generic

then restarted the upgrade process:
$ sudo apt-get upgrade
and as last step moved the original script back to  /usr/sbin/mkinitramfs :
$ sudo rm /usr/sbin/mkinitramfs
$ sudo mv /usr/sbin/mkinitramfs.org /usr/sbin/mkinitramfs
well not pretty, but it worked :-)

---

### Post by MoehMan on 2007-11-07
> **Critias said:**
> I had the same problem, used a quick and dirty hack to solve it:
moved mkinitramfs out of the way:
$ sudo mv /usr/sbin/mkinitramfs /usr/sbin/mkinitramfs.org
and placed my own little script there that called /usr/sbin/mkinitramfs.org with the Right parameters:
$ sudo vim /usr/sbin/mkinitramfs

#!/bin/bash
/usr/sbin/mkinitramfs.org -v -o /boot/initrd.img-2.6.22-14-generic -k 2.6.22-14-generic

then restarted the upgrade process:
$ sudo apt-get upgrade
and as last step moved the original script back to  /usr/sbin/mkinitramfs :
$ sudo rm /usr/sbin/mkinitramfs
$ sudo mv /usr/sbin/mkinitramfs.org /usr/sbin/mkinitramfs
well not pretty, but it worked :-)

worked for me. After doing the apt-get upgrade, there was no "initrd" line written in the grub configuration, but after manually adding it, everything works great now. Thanks! :)

---

### Post by vouzico on 2007-11-08
I get this error message after the apt-get upgrade : 

Could not find postinst hook script [update-grub].

---

### Post by zatarc on 2007-11-17
> **Critias said:**
> I had the same problem, used a quick and dirty hack to solve it:
moved mkinitramfs out of the way:
$ sudo mv /usr/sbin/mkinitramfs /usr/sbin/mkinitramfs.org
and placed my own little script there that called /usr/sbin/mkinitramfs.org with the Right parameters:
$ sudo vim /usr/sbin/mkinitramfs

#!/bin/bash
/usr/sbin/mkinitramfs.org -v -o /boot/initrd.img-2.6.22-14-generic -k 2.6.22-14-generic

then restarted the upgrade process:
$ sudo apt-get upgrade
and as last step moved the original script back to  /usr/sbin/mkinitramfs :
$ sudo rm /usr/sbin/mkinitramfs
$ sudo mv /usr/sbin/mkinitramfs.org /usr/sbin/mkinitramfs
well not pretty, but it worked :-)

> **MoehMan said:**
> worked for me. After doing the apt-get upgrade, there was no "initrd" line written in the grub configuration, but after manually adding it, everything works great now. Thanks! :)

Works like a charm. Grub autoconfiguration was fine here (for the first time ever I think - cryptoroot). thx :)

---

### Post by kristus on 2007-12-22
I got this problem and invented a similar ugly workaround right after upgrading to gutsy when it was released and I'm still plagued by it (it reappears after every kernel image upgrade). Now, after the upgrade it's complaining about the missing u parameter instead of c, but if you look at the post-installation scripts you'll see that it's the same problem, just differing in that

Obviously, something must be wrong with **our** installations since the vast majority of *ubuntu users (I use kubuntu, but that shouldn't make any difference) are not complaining. Thus, it can't be the kernel package that is broken by calling mkinitramfs with an incorrect parameter. I also doubt that it's mkinitramfs that's broken for the same reason. But what can possibly be the problem then?

The only way I'm deviating from your average kubuntu installation is that I use full hard drive encryption, but that's completely irrelevant. Also, I initially installed the Feisty release and then upgraded to Gutsy, then got the problems.

---

### Post by kristus on 2007-12-22
Just found about this configuration file: /etc/kernel-img.conf where you can specify which ramdisk update script it should use. Just change the line beginning with "ramdisk = [...]" to "ramdisk = /usr/sbin/update-initramfs"

---

### Post by Critias on 2008-01-03
> **kristus said:**
> Just found about this configuration file: /etc/kernel-img.conf where you can specify which ramdisk update script it should use. Just change the line beginning with "ramdisk = [...]" to "ramdisk = /usr/sbin/update-initramfs"

Worked fine and is way better then my workaround :-)

> **kristus said:**
> 
Obviously, something must be wrong with **our** installations since the vast majority of *ubuntu users (I use kubuntu, but that shouldn't make any difference) are not complaining. Thus, it can't be the kernel package that is broken by calling mkinitramfs with an incorrect parameter. I also doubt that it's mkinitramfs that's broken for the same reason. But what can possibly be the problem then?

Well I'm using kubuntu and cryptoroot maybe that has something to do with it...

---

### Post by jav on 2008-01-21
> **Critias said:**
> I had the same problem, used a quick and dirty hack to solve it:
moved mkinitramfs out of the way:
$ sudo mv /usr/sbin/mkinitramfs /usr/sbin/mkinitramfs.org
and placed my own little script there that called /usr/sbin/mkinitramfs.org with the Right parameters:
$ sudo vim /usr/sbin/mkinitramfs

#!/bin/bash
/usr/sbin/mkinitramfs.org -v -o /boot/initrd.img-2.6.22-14-generic -k 2.6.22-14-generic

then restarted the upgrade process:
$ sudo apt-get upgrade
and as last step moved the original script back to  /usr/sbin/mkinitramfs :
$ sudo rm /usr/sbin/mkinitramfs
$ sudo mv /usr/sbin/mkinitramfs.org /usr/sbin/mkinitramfs
well not pretty, but it worked :-)

This worked for me after I added the following (before apt-get update)
```

sudo chmod u+x /usr/sbin/mkinitramfs
sudo mv /initrd.img /initrd.img.javbak
sudo mv /vmlinuz.img /vmlinuz.img.javbak

```

I did not have any luck with the "ramdisk = (something)" solution :(

Anyway, problem solved for me :)

---

