---
title: "boot-repair failure"
date: 2017-08-15
forum: MINT
---

### Post by Stanley Krute on 2017-08-15
Hello 

I boot Windows and Linux on a Lenovo T520. All was well, until I deleted a Windows partition. I could no longer boot. 

I ran boot-repair, and now I can boot into Windows. But Linux is still a fail. 

boot-repair stored data on its fix here :  [http://paste.ubuntu.com/25317332/](http://paste.ubuntu.com/25317332/)

here are the contents of my fstab file : 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=1f56a3b5-717e-482b-9293-2ff94d16b457 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
#UUID=9e035c73-19fd-4c85-a828-3e0f8e871e69 /boot           ext2    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=bdc69c3f-79b6-4939-84cf-f1dc80b0d434 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=92123073-4120-4ee6-b939-57de345a464c none            swap    sw              0       0
UUID=9e035c73-19fd-4c85-a828-3e0f8e871e69	/boot	ext2	defaults	0	2
```

I used gparted to verify that all those UUIDs for my /, /boot, /home, and swap partitions are correct. 

Here's a picture of the failure I get when I try to boot into Linux :
 [IMG]http://www.skcaps.com/debug/linux.boot.fail.jpg[/IMG]


Anyone have any thoughts ??

thanks 

stan

---

### Post by sotiris2 on 2017-08-15
Your boot partition is 100% full. Maybe a kernel installation was only partially completed? Can you boot an older kernel? 
What's up with that gap in device names sdb to sdg ? How many actual drives do you have?

---

### Post by Stanley Krute on 2017-08-15
Yes, a kernel installation failed due to lack of space. 

I'll try to boot an older kernel. 

One actual drive in the computer, several other external drives attached via USB. 

Thx for speedy thoughts !

---

### Post by Stanley Krute on 2017-08-15
aha !!  I booted the previous kernel, and I'm back in business. Thanks SO MUCH !!

Any suggestions on safest way to expand boot partition and perhaps get rid of some of the older kernels ??

---

### Post by sotiris2 on 2017-08-15
I manually delete the files of older kernels and run update-grub myself. That said here is [community's wiki](https://help.ubuntu.com/community/RemoveOldKernels) with more complete advice.

Expanding the boot partition would require you to move whatever is to the "right" of it so a live media and probably a lot of time (all of the data in the partition after it need to be read and copied a bit to the "right")

---

### Post by Stanley Krute on 2017-08-15
Thanks again. I used boot-repair-disk to resize /boot after shrinking the partition following it a bit. Worked very speedily -- this system has a nice 250GB SSD and an i7 processor. 

Now I'll use your advice and the link you provided to get rid of older kernels. 

I so heart Linux !!!

---

### Post by ajgreeny on 2017-08-15
Firstly, do not manually start removing any kernel files from the /boot partition or you may make your system very unstable and create further difficulties with kernel installations in future.  Unless you know exactly what you're doing and how to solve those extra problems, you should always use the package-manager to install or remove kernels.

So we know which kernels you have installed and the status of each please run terminal command ```
dpkg -l linux-image*
``` and copy back here the output you see, in code tags, please.

My hope is that we can then remove a few unwanted kernels, make some space and run ```
sudo apt-get autoremove
``` to clean up the rest; that autoremove command will not do anything if there is insufficient space as it needs a lot of headroom to succeed.

---

### Post by ajgreeny on 2017-08-15
*Thread moved to **MINT**.* which is more appropriate and a better fit, as you are running Mint 18.2, not Ubuntu..

---

### Post by vasa1 on 2017-08-15
> **ajgreeny said:**
> *Thread moved to **MINT**.* which is more appropriate and a better fit, as you are running Mint 18.2, not Ubuntu..+1

OP, in future, please be clear about the distro instead of referring to "Linux". It'll help others help you better.

---

### Post by Stanley Krute on 2017-08-16
Thanks for the help at all levels. 

Unfortunately, I started doing manual uninstalls using the info on the page sotiris2 linked to. No major problems, but some errors. For example :

```
sudo dpkg --purge linux-headers-4.4.0-53-generic
(Reading database ... 383755 files and directories currently installed.)
Removing linux-headers-4.4.0-53-generic (4.4.0-53.74) ...
dpkg: warning: while removing linux-headers-4.4.0-53-generic, directory '/lib/modules/4.4.0-53-generic' not empty so not removed

```

Ideas on how to fix that one ?

---

### Post by Stanley Krute on 2017-08-16
Here's the info ajgreeny requested :

```
dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
ii  linux-image-4. 4.10.0-27.30 amd64        Linux kernel image for version 4.
in  linux-image-4. <none>       amd64        (no description available)
ii  linux-image-4. 4.10.0-32.36 amd64        Linux kernel image for version 4.
un  linux-image-4. <none>       <none>       (no description available)
un  linux-image-4. <none>       <none>       (no description available)
ii  linux-image-4. 4.8.0-53.56~ amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.8.0-58.63~ amd64        Linux kernel image for version 4.
ii  linux-image-ex 4.10.0-27.30 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-28.32 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.10.0-32.36 amd64        Linux kernel extra modules for ve
pH  linux-image-ex 4.4.0-53.74  amd64        Linux kernel extra modules for ve
rH  linux-image-ex 4.4.0-83.106 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.8.0-53.56~ amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.8.0-58.63~ amd64        Linux kernel extra modules for ve

```

---

### Post by Stanley Krute on 2017-09-01
Never heard back, so I googled lots more, tried a bunch of stuff, nothing worked. 

So I just saved all my data and reinstalled freshly. All is now well. 

Thanks everyone for your assistance. I've learned a lot about multiple kernels and keeping them trimmed up.

---

