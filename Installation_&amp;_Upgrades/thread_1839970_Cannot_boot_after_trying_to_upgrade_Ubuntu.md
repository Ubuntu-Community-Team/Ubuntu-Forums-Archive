---
title: "Cannot boot after trying to upgrade Ubuntu"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by heatdav on 2011-09-06
Hi. I recently tried to upgrade my Hardy Heron version of Ubuntu. The upgrade seemed to be going ok, but as soon as my computer restarted, it will no longer boot. I get as far as the boot loader and I get the text below, at which point the computer freezes (I can't type anything). 

I have been led to believe that this is a problem with "the boot loader pointing to the wrong kernel" or something like that, and other people seem to have had this same problem, but I am a complete newbie to all but the most basic functionality of linux, so have been completely unable to follow their instructions to fix it. Please help and can you make any instructions super-simple as I really won't follow any linux terminology!




Starting up ...
Uncompessing Linux... Ok, booting the kernel.
mount: mounting none on /dev failed: No such device
udevd[505]: error getting socket: Invalid argument

error initializing netlink socket
udevd[505]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
  - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by MAFoElffen on 2011-09-06
> **heatdav said:**
> Hi. I recently tried to upgrade my Hardy Heron version of Ubuntu. The upgrade seemed to be going ok, but as soon as my computer restarted, it will no longer boot. I get as far as the boot loader and I get the text below, at which point the computer freezes (I can't type anything). 

I have been led to believe that this is a problem with "the boot loader pointing to the wrong kernel" or something like that, and other people seem to have had this same problem, but I am a complete newbie to all but the most basic functionality of linux, so have been completely unable to follow their instructions to fix it. Please help and can you make any instructions super-simple as I really won't follow any linux terminology!

```

Starting up ...
Uncompessing Linux... Ok, booting the kernel.
mount: mounting none on /dev failed: No such device
udevd[505]: error getting socket: Invalid argument
error initializing netlink socket
udevd[505]: error initializing netlink socket
libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
  - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does not exist. Dropping to a shell!
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

```
Okay, so... you upgraded from Ubuntu 8.04 to 8.10.  Having been 8.04 wasn't supported for awhile, you must have a lot of things installed and personalized on your's eh?  8.04 used an ext3 filesystem and 8.10 used a ext4 filesyetem... but as I remeber they were backward compatible(?).

Can you run a 8.10 LiveCD and see the drive?   If so, you could mount the installed system, update, upgrade, (which will most likely update the kernel) and renew the grub menu.

Edit-- I saw the request for detailed instructions... 
1. Boot up on the same versioned LiveCD

2. Find your "partition and drive, e.g. /dev/sda5 (where you've installed Ubuntu ... as Ubuntu see's as the "/" partition)
```

sudo mount /dev/sda5 /mnt

```3. If you have a dedicated boot partition: sudo mount /dev/sda3 /mnt/boot
```

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

```4. "changeroot" to /mnt
```

sudo chroot /mnt /bin/bash

```5. Now you're "on" Ubuntu, see chnageroot man page for details
```

sudo apt-get update
sudo apt-get upgrade

``` 
The upgrade should install the newest kernel and in doing that, retrigger the grub menu to rebuild.

---

### Post by garvinrick4 on 2011-09-06
Wrong thread.

---

### Post by heatdav on 2011-09-15
Hi MaFoElffen. Sorry for the delay in responding to your reply. I  managed to get hold of a version 11 liveCD, which is clearly several  versions ahead of what's on there, but it seemed to load ok and the  commands you gave me seemed to execute. 

However, when I ran the upgrade command, certain error messages  appeared, firstly to do with having run out of disk space, but after  tidying that up, and rerunning the upgrade command, I eventually got to  this message

>  root@ubuntu:/# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-image-generic sound-juicer
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

I tried shutting down, but the computer is reluctant to shut down properly from the liveCD, so after rebooting with the power button, the same error message came up as before

Any ideas? Again, please be as explicit as possible with any instructions because my Linux knowledge is pretty basic!

Many thanks

---

### Post by heatdav on 2011-09-15
OK, looks like I managed to fix it. I ran > sudo apt-get dist-upgrade and that forced the kernel to update. Thanks for your help! Much appreciated

---

### Post by mörgæs on 2011-09-15
After finding the solution, please mark the thread 'solved'. I have done it this time.

I noticed that you have a root account. This might be interesting to you:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

