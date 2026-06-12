---
title: "[SOLVED] Fail to boot off RAID device - help !"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2007-12-27
I'm having a silly amount of trouble getting RAID-1 running on my Gutsy server. I have two identical IDE 300Gb drives, and have done everything I think needs to be done to create three degraded RAID-1 arrays (brief outline of what I did at the end of this post). However when I reboot off the second drive in order to add the partitions on the first into the arrays, the following screen appears, takes about 3 minutes to get past "Loading, please wait":

```
Booting 'Ubuntu 7.10, kernel 2.6.22-14-server'

root (hd0,0)
  Filesystem type is ext2fs, partition type 0xfd
kernel /boot/vmlinuz-2.6.22-14-server root=/dev/md0 acpi=off ro quiet splash
    [Linux-bzImage, setup=0x1e00, size=01b2538]
initrd /boot/initrd.img-2.6.22-14-server
    [Linux-initrd @ 0x1f83b000, 0x7b499b bytes]

Loading, please wait...
         Check root= bootarg cat /proc/cmdline
         or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/md0 does not exist. Dropping to a shell!
```

It then drops into BusyBox. I can understand why /dev/md0 might not exist at that time in the cycle, but I've also tried specifying /dev/sdb1, and "root=UUID=<the UUID for /dev/sdb1>". and neither works.

I'm obviously missing something here - any help very welcome !

-----------------------------------------------------------------------------------------------------------------------------------
What I did:

1. First drive (primary master) has /dev/sda1 (/), /dev/sda6 (/home), /dev/sda5 (swap) partitions, fully working;
2. Installed second drive as secondary slave
3. Partitioned second drive exactly the same as the first (/dev/sdb1 on /, /dev/sdb5 on swap, /dev/sdb6 on /home). Change each partition to type FD (Linux raid autodetect. fdisk -lu shows both drives identical.
4. mdadm three devices: /md0 (for /), /dev/md1 (for swap), /dev/md2 (for /home), each as a degraded array. cat /proc/mdstat shows the arrays up and running.
5. e2fsck and resize2fs /dev/md0 and /dev/md1.
6. mkswap /dev/md1, mount /md0 as /mnt, mount /md2 as /mnt/home. Copy the filesystems on the first disk to the corresponding ones on the second. All files check out OK.
7. install grub on the second drive:
# grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
8. Edit the fstab on the second drive:
/dev/md0   /       ext3    errors=remount-ro       0       1
/dev/md1   none    swap    sw                      0       0
/dev/md2   /home   ext3    errors=remount-ro       0       2
9. Edit the /boot/grub/menu.lst file on the second drive, set the boot device to /dev/md0:
...
kernel /boot/vmlinuz-2.6.22-14-server root=/dev/md0 acpi=off ro quiet splash
...
10. Reboot off the second drive (specified in BIOS).

---

### Post by tgilber1 on 2007-12-27
It looks like you may not have loaded the raid1 module in your initramfs. 

1.  Make sure that raid1 is populated in the initramfs
2.  sudo vi /etc/initramfs-tools/modules 
2.  If not, make correction and update your initramfs
3.  sudo  sudo update-initramfs -u
4.  Reboot

---

### Post by dbyrne on 2007-12-27
Thanks - I'll give that a shot. I think I have the raid1 module loaded, even though it's commented out in the /etc/initramfs-tools/modules. I don't know what the best way to find out is, but the following suggests it's already there:

$ cat /proc/modules | grep raid1
raid10 26496 0 - Live 0xf8886000
raid1 25856 3 - Live 0xf8861000
md_mod 82324 8 raid10,raid456,raid1,raid0,multipath,linear, Live 0xf886a000
$

Would that same cat command at the BusyBox prompt confirm that the raid1 module is loaded ?

Anyway I'll try out the update-initramfs idea, presumably then I guess I need to copy the regened kernel and initrd over to the second drive first before rebooting ?

---

### Post by dbyrne on 2007-12-28
I followed the steps in my last post, and then set up grub again with different parameters:

# grub
grub> device (hd1) /dev/sdb
grub> root (hd1,0)
grub> setup (hd1)
grub> quit

(Note: hd1 instead of hd0). I'll have to look into this a bit more as several sites on setting up RAID specifically say to set up the second drive as hd0.

Anyway, one of these steps did the trick, system came up first time on the second drive and I was able to complete building the arrays with mdadm -a.

Thanks tgilber1 for your help !

---

### Post by tgilber1 on 2007-12-28
> **dbyrne said:**
> I followed the steps in my last post, and then set up grub again with different parameters:

# grub
grub> device (hd1) /dev/sdb
grub> root (hd1,0)
grub> setup (hd1)
grub> quit

(Note: hd1 instead of hd0). I'll have to look into this a bit more as several sites on setting up RAID specifically say to set up the second drive as hd0.

Anyway, one of these steps did the trick, system came up first time on the second drive and I was able to complete building the arrays with mdadm -a.

Thanks tgilber1 for your help !

If you did not issue a "setup (hdx)" x=to driver number, on the second drive, then that was a problem.  The setup writes to the MBR of the disk.  The second one would have never boot up by itself no matter what modules you would have loaded.

As for the "/etc/initramfs-tools/modules" file, this file allows you to plug in modules into the kernel during bootup.  Otherwise, unless the raid1 is built into the kernel directly, the kernel could not boot up raid.

To see if a driver is built into the kernel as module or directly, you can check it by viewing the following hidden file:  /usr/src/linux-headers-2.6.22-14-generic/.config

"ls -a" to view hidden files

If it is a module, it will have the letter 'M' after it.  If built directly into kernel, it will have the letter 'y'

---

### Post by dbyrne on 2008-01-21
Looks like I spoke too soon on this one - I'm not quite there yet !

Even though the system has been working fine since I got the RAID-1 set up, and "cat /proc/mdstat" shows everything working, I've found that the system will only boot with both drives powered up and connected. If I disconnect either drive it won't boot.

I get exactly the same output regardless of which drive is disconnected (see below): note the *root (hd0, 0)* for both, shouldn't it read hd1 for one of them ?

Also, it's trying to boot off /dev/md0, is that possible if it can't assemble the array ?

:confused::confused::confused::confused:

```
Booting 'Ubuntu 7.10, kernel 2.6.22-14-server'

root (hd0,0)
  Filesystem type is ext2fs, partition type 0xfd
kernel /boot/vmlinuz-2.6.22-14-server root=/dev/md0 acpi=off ro quiet splash
    [Linux-bzImage, setup=0x1e00, size=01b2538]
initrd /boot/initrd.img-2.6.22-14-server
    [Linux-initrd @ 0x1f83b000, 0x7b499b bytes]

Loading, please wait...

stdin: error 0
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
mount: can't read /etc/fstab: No such file or directory
mount: mounting /root/dev on /root/sys/.static/dev failed: No such file or directory
mount: mounting /root/sys on /root/sys/.static/sys failed: No such file or directory
mount: mounting /root/proc on /root/sys/.static/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Busybox v1.1.3 etc.etc.

(initramfs)
```

---

### Post by bsmith1051 on 2008-03-04
> **dbyrne said:**
> Even though the system has been working fine since I got the RAID-1 set up, and "cat /proc/mdstat" shows everything working, I've found that the system will only boot with both drives powered up and connected. If I disconnect either drive it won't boot.
Any update on this?  I think I'm experiencing the same thing as you.

I'm trying to get comfortable with using RAID1 and my first test was simply to disconnect the 2nd drive.  The system starts to boot but then fails to load the array (md0) and halts.  Shouldn't it simply load md0 as 'degraded' ?

---

### Post by bsmith1051 on 2008-03-05
Actually, it looks like this is a known bug with Ubuntu 7.10 and earlier!
[https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375)

---

### Post by bsmith1051 on 2008-04-09
FYI
A workaround has been posted in the previously-mentioned bug's discussion.  Basically, you add another step to the init scripts, then update the boot image to include it.  If you unexpectedly lose a drive (or unplug one as a test) then the extra scripting will boot the array in degraded mode rather than giving up.

---

