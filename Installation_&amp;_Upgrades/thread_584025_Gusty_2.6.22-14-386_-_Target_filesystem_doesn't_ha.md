---
title: "Gusty 2.6.22-14-386 - Target filesystem doesn't have /sbin/init"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Temujin_12 on 2007-10-20
After pushing my way through the update manager, I now have a halfway-working Gusty (Kubuntu) upgrade from Feisty.  There are other problems I need to figure out, but this thread is about the 2.6.22-14-386 kernel that the upgrade installed.

First some info:

$lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0e.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 0c)
00:0f.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
00:0f.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
```


/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=212ba01c-f606-4b80-a3c0-2c34aea29bbe none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

/boot/grub/device.map:
```
(hd0)   /dev/hdb
```

$mount
```
/dev/evms/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

/boot/grub/menu.lst
```
default		0
timeout		3
hiddenmenu

title		Ubuntu, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
savedefault

title		Ubuntu, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.15-25-386

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=4a73b73b-8428-45f4-ac89-fcc967ad96c3 ro single
initrd		/boot/initrd.img-2.6.15-23-386

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
```

Whenever I try to boot using the 2.6.22-14-386 kernel, I get the following:
```
Begin: Running /scripts/local-premount ...
kinit: name_to_dev_t(/dev/disk/by-uuid/212ba01c-f606-4b80-a3c0-2c34aea29bbe) = hd5(3,69)
kinit: trying to resume from /dev/disk/by-uuid212ba01c-f606-4b80-a3c0-2c34aea29bbe
[31.196052] Attempting manual resume
kinit: No resume image, doing normal boot ...
Done.
mount: Mounting /dev/disk/by-uuid/4a73b73b-8428-45f4-ac89-fcc967ad96c3 on /root failed: Device or resource busy
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys faied: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I've spent a few hours looking around for an answer but most seem to point to a bad hard drive which I'm sure is not the case since booting to my the 2.6.20-16-386 kernel works just fine (loads in to KDE and everything).

Anyone have any ideas?

For now, I'm just booting to the 2.6.20-16-386 kernel.  If I configure xgl and compiz while booted into the 2.6.20-16-386 kernel will that affect the 2.6.22-14-386 kernel if/when the above issue is fixed?

---

### Post by Temujin_12 on 2007-10-21
Sorry to bump this one up, but I won't be able to do any fancy NVIDIA stuff until I can boot into the latest kernel since installing restricted modules and NVIDIA drivers all seem to want to use this latest kernel.

IOW:
```
$sudo apt-get install linux-restricted-modules-2.6.20-16-386
Package linux-restricted-modules-2.6.20-16-386 is not available, but is referred to by another package.
This may mean that the packages is missing, has been obsoleted, or is only available from another source
```

I want to get going with compiz-fusion but I either need to get the 2.6.22-14-386 kernel booting properly or get the drivers installed and working with the 2.6.20-16 kernel.

---

### Post by Temujin_12 on 2007-10-21
One last bump to see if anyone can help before I go somewhere else to look.

---

### Post by ziptiespec on 2007-10-22
I was having the same issue.  Here is how I fixed it:

[LIST=1]
[*]Boot to LiveCD
[*]Open terminal
[*]Type fdisk -l to see which partition has Linux installed (/dev/sda1 in my case)
[*]Type sudo mount /dev/sda1 /mnt (your partition may be different, replace sda1 as needed)
[*]sudo mount -t proc proc /mnt/proc
[*]sudo chroot /mnt
[*]sudo aptitude purge evms
[*]sudo update-initramfs -u -k 2.6.22-14-386
[*]reboot
[*]eject LiveCD
[/LIST]

I found this here:
[http://ubuntuforums.org/showthread.php?t=497941](http://ubuntuforums.org/showthread.php?t=497941)

I used this search:
gutsy device resource busy target filesystem doesn't have /sbin/init

---

### Post by Temujin_12 on 2007-10-22
> **ziptiespec said:**
> I was having the same issue.  Here is how I fixed it:

[LIST=1]
[*]Boot to LiveCD
[*]Open terminal
[*]Type fdisk -l to see which partition has Linux installed (/dev/sda1 in my case)
[*]Type sudo mount /dev/sda1 /mnt (your partition may be different, replace sda1 as needed)
[*]sudo mount -t proc proc /mnt/proc
[*]sudo chroot /mnt
[*]sudo aptitude purge evms
[*]sudo update-initramfs -u -k 2.6.22-14-386
[*]reboot
[*]eject LiveCD
[/LIST]

I found this here:
[http://ubuntuforums.org/showthread.php?t=497941](http://ubuntuforums.org/showthread.php?t=497941)

I used this search:
gutsy device resource busy target filesystem doesn't have /sbin/init

Worked like a charm!  Thanks!

Now to get NVIDIA drivers and compiz working.... but I'll start another thread on that if I need help.

---

