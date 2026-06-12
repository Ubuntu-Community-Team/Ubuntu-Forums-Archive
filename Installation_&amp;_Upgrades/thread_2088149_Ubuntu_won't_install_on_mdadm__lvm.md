---
title: "Ubuntu won't install on mdadm / lvm"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Sam1994 on 2012-11-25
Hi,
 
Outline:
 
Precise netboot image
LVM
mdadm
 
I'm really confused about installing Ubuntu. This is my first go with mdadm and LVM. And I am convinced Ubuntu does not support LVM/mdadm.
 
The first attempt, I had one logical volume (/) which I installed to, and that seemed to work. It then failed at the grub --install stage. I concluded that GRUB must need to be installed outside of LVM then. So now:
 
I booted ubuntu off usb, set up mdadm on my raid, added an ext4 partition of 500M or so, and setup LVM. PXE'd back into netboot and tried again. This time the kernel refuses to install as does GRUB. I finished the install anyway and tried to chase down the issues through chroot:
 
Seems Linux-image-generic will not install and it fails on its post install script. Error (after tracing with bash -x), is with
 
mkinitramfs -o /boot/initrd.img-3.2.0-33-generic.new 3.2.0-33-generic  
 
it gives me:
 
```
 
+ minor=0
++ ls -1 /sys/block/dm-0/slaves
++ head -n 1
+ block=md126p2
+ '[' md126p2 '!=' md126p2 ']'
+ '[' 126p2 '!=' md126p2 ']'
++ sed -ne 's/multipath/[/' -e 's/linear/[/' -e 's/raid[0-9][0-9]*/[/' -e 's/\([hs]d[a-z][a-z]*\)[0-9][0-9]*/\1/g' -e '/^md126p2 :/s/^[^[]*\[ \([^\[]*\)\[.*$/\1/p'
+ block=
+ '[' '' '!=' '' ']'
+ '[' '' '!=' '' ']'
+ block=
+ '[' -z '' ']'
+ echo 'mkinitramfs: for root /dev/dm-0 missing  /sys/block/ entry'
mkinitramfs: for root /dev/dm-0 missing  /sys/block/ entry
+ echo 'mkinitramfs: workaround is MODULES=most'
mkinitramfs: workaround is MODULES=most
+ echo 'mkinitramfs: Error please report the bug'
mkinitramfs: Error please report the bug
+ exit 1
[EMAIL="root@ubuntu:/etc/initramfs-tools/scripts"]root@ubuntu:/etc/initramfs-tools/scripts[/EMAIL]# which
[EMAIL="root@ubuntu:/etc/initramfs-tools/scripts"]root@ubuntu:/etc/initramfs-tools/scripts[/EMAIL]# which nano
/usr/bin/nano
[EMAIL="root@ubuntu:/etc/initramfs-tools/scripts"]root@ubuntu:/etc/initramfs-tools/scripts[/EMAIL]# mkinitramfs -o /boot/initrd.img-3.2.0-33-generic.new 3.2.0-33-generic
mkinitramfs: for root /dev/dm-0 missing  /sys/block/ entry
mkinitramfs: workaround is MODULES=most
mkinitramfs: Error please report the bug

```
 
I can confirm that dm-0 is present in both /dev and /sys/block.
 
Not sure what is causing this. Or why GRUB failed. It seems OK now it is outside of LVM though.
 
Here is my partition layout:
```
 
 
[EMAIL="root@ubuntu:~/mount"]root@ubuntu:~/mount[/EMAIL]# parted -s /dev/md126 print
Model: Linux Software RAID Array (md)
Disk /dev/md126: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Number  Start   End     Size    File system  Name     Flags
 1      4194kB  600MB   596MB   ext4         primary  boot
 2      604MB   2000GB  2000GB               primary

```
 
There is one partition (150GB). And I installed root to /dev/mapper/vg00-OS.
 
Thanks in advance

---

### Post by darkod on 2012-11-25
Which ISO are you using for install/netboot? The Alternate ISO supports mdadm software raid and LVM. The standard desktop ISO (live cd) doesn't support them by default but the packages can be added in live mode and it should work if you continue installing without rebooting.

The bootloader, grub, goes to the MBR of the disks, not inside any partition. If you use raid0, you have to create separate /boot partition outside the array. For raid1 that's not needed.

For LVM earlier separate /boot was also needed outside the LVM but the latest versions can work without this.

So, for example, if you are setting up LVM on top of raid1, there is no need to have separate /boot partition otuside the array/LVM. The grub bootloader will go to the MBRs of both disks, /dev/sda and /dev/sdb.

But you will have to use the alternate cd/iso for the PXE boot and to install.

---

### Post by Sam1994 on 2012-11-25
> **darkod said:**
> Which ISO are you using for install/netboot? The Alternate ISO supports mdadm software raid and LVM. The standard desktop ISO (live cd) doesn't support them by default but the packages can be added in live mode and it should work if you continue installing without rebooting.
 
The bootloader, grub, goes to the MBR of the disks, not inside any partition. If you use raid0, you have to create separate /boot partition outside the array. For raid1 that's not needed.
 
For LVM earlier separate /boot was also needed outside the LVM but the latest versions can work without this.
 
So, for example, if you are setting up LVM on top of raid1, there is no need to have separate /boot partition otuside the array/LVM. The grub bootloader will go to the MBRs of both disks, /dev/sda and /dev/sdb.
 
But you will have to use the alternate cd/iso for the PXE boot and to install.
 
Hi
 
I literally grabbed a netboot of precise. So this one:
 
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)
 
I'm using RAID1. But anywho, I've resorted to a separate partition because GRUB was saying something about unable to install within a system block.
 
Will an alternate definitely help then? My confusion:
 
if the standard install doesn't support it, why does the partitioner offer these as options?
 
how come it still does not work properly when I chroot in and try apt-get -f install to fix the kernel packages. I can understand maybe the installer missing some modules, but is there something not being installed as well? Curious as I may just go the debootstrap route at this rate
 
Thanks

---

### Post by darkod on 2012-11-25
I don't know whether the netboot can download the needed packages or not. The alternate does work for mdadm and lvm installs, that's for sure.

I thought you are trying to do PXE install from one to another computer. If that's not what you need, I suggest the alternate cd instead of netboot.

---

### Post by Sam1994 on 2012-11-25
> **darkod said:**
> I don't know whether the netboot can download the needed packages or not. The alternate does work for mdadm and lvm installs, that's for sure.
 
I thought you are trying to do PXE install from one to another computer. If that's not what you need, I suggest the alternate cd instead of netboot.
 
I'll try the alternate cd and let you know how it goes.
 
Thanks!

---

