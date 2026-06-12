---
title: "Cannot boot Kubuntu 7.10 after upgrade"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by ulriks on 2007-11-13
Hello everyone,

I have just upgraded to 7.10. During upgrade there were issues with  libavutil-dev (I think - or libavcodec-dev?), which I installed manually, did consistency checks with apt-get, and a dist-upgrade - also with apt-get.

Now I cannot boot. Instead I end up in Busybox/ash. As far as I can tell from the following (when doing ctrl-alt-F1 on boot), Grub is not pointing to the correct place:

```
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=f2b021cf-4a37-4755-b482-5a59a0262a23 ro quiet splash
initrd /boot/initrd.img-2.6-14-386
Loading, please wait...
[  283.633160 ata1: SRST failed (errorno=-16)
      Check root=bootarg cat /proc/cmdline
      or missing modules, devices: cal /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/f2b021cf-4a37-4755-b482-5a59a0262a23 does not exist
```

How do I fix it?

Thanks a lot!
Ulrik

---

### Post by dezoete on 2007-11-13
Hi

I had a simillar problem, while installing Ubuntu 7.10
In my case the computer insisted on starting in the windows XP 
Someone here (Bulldog) advised me to check if the Ubuntu hard disk was the first boot up disk....:lolflag:

This indeed was the problem

---

### Post by ulriks on 2007-11-13
I only run Ubuntu and with a seperate, older harddisk used only for backup. I will check is the primary drive is still the boot up, but how could an upgrade change that?

---

### Post by ulriks on 2007-11-14
I have no issues booting into 2.6.20-16-386, so I did and reinstalled the  2.6.22-14-386. This didn't work....

Any other ideas on how to fix a broken version upgrade?

---

### Post by charleseddy on 2007-11-14
I just had a similar problem.  While I can't be 100% sure of this, I'm pretty sure 7.10 has an issue with upgrading while you have two hard drives.  Since there won't be any data lost, unplug the slave drive, install kubuntu again (probably 25-30 minutes tops), then reboot, plug your 2nd drive in.  Should be no problems.  Let me know how it works, because I'm pretty sure this is the root of your error.  ce

---

### Post by bulldog on 2007-11-14
You can start with a simple```
sudo update-grub
```
If this is not the solution,you'll have to do it manual.


Find your partition uuid```
ls /dev/disk/by-uuid -lh
```
Got to the menu.lst [make a copy first]
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
gksu gedit /boot/grub/menu.lst
```
and check if the uuid is the same as you found with the first command.
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d6a04dea-7971-4d54-b0de-9c94a65fd56d ro


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6a04dea-7971-4d54-b0de-9c94a65fd56d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6a04dea-7971-4d54-b0de-9c94a65fd56d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
```

If not,change them to the one you found.

---

### Post by ulriks on 2007-11-14
Thanks - I will try it as soon as I get back from a weekend away from my computer

---

### Post by ulriks on 2007-11-21
Sorry for the lag-time.

Doing as sugested I get:
```

ls /dev/disk/by-uuid -lh
total 0
lrwxrwxrwx 1 root root 10 2007-11-21 07:42 751cc55c-d0dc-4a80-b0f4-4092c7f793e9 -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-11-21 07:42 93e540be-b86d-4f39-af38-3e534346db7c -> ../../hdc1
lrwxrwxrwx 1 root root 10 2007-11-21 07:42 f2b021cf-4a37-4755-b482-5a59a02b2a23 -> ../../hda1

```

My menu.lst looks like:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f2b021cf-4a37-4755-b482-5a59a02b2a23 ro

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=f2b021cf-4a37-4755-b482-5a59a02b2a23 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=f2b021cf-4a37-4755-b482-5a59a02b2a23 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=f2b021cf-4a37-4755-b482-5a59a02b2a23 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
```

I still get the error -16 when I boot into 2.6.22-14-386.

Could it be that something in the configuration when I upgraded went wrong? How do I reconfigure my system?

Ulrik

---

