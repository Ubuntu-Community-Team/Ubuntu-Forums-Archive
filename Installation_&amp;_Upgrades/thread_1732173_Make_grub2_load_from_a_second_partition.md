---
title: "Make grub2 load from a second partition"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by GregoryMA on 2011-04-17
So I have this 7 year old laptop.  It is obviously slow but it works pretty well, xcept that the CD drive and the USB ports have gone to meet their makers.  I am currently running Ubuntu 10.04 but I want to install a lightweight non-ubuntu distro.  Something slim and trim so this aging guy can keep up.  I found this how-to ([https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)) which explains how to put the installation file on a second partition and then get grub (or rather grub2 in this situation) to load from the second partition.  Well, I have the second partition set-up with the installation iso in it.  The only trouble is that I can't figure out how to make grub2 boot from the second partition.  If there is anyone out there who is better at tinkering with this stuff than me please help me out.  /dev/sda5 is the partition which has the installation iso on it and where I want grub2 to boot from.  Here is some info.

sudo fdisk -l 
```
gregory@box:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e4fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19267   154754048   83  Linux
/dev/sda2           19267       19458     1533953    5  Extended
/dev/sda5           19267       19458     1532928   83  Linux

```

/etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2def1ea-a8b9-47d2-9ae1-27c11dd5bdb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=89ec501b-4a00-4cfb-b2a5-e41b3113f034 none            swap    sw              0       0
UUID=52a0f55c-4ce9-4400-9b6f-a1907f3ac1ec   /media/house    ext4          nodev,nosuid       0       2 
```

/etc/grub.d/40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "installer" {
        insmod ext2
        set root=(hd0,5)
        linux /casper/vmlinuz boot=casper root=/dev/ram1 ramdisk_size=1048576 rw
        initrd /casper/initrd.lz
}
```

---

### Post by Dutch70 on 2011-04-17
See if this helps you out. What concerns me though, is how are you going to fix it if something goes wrong.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202[/COLOR]]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")

I think the command you're looking for is...
```
sudo grub-install /dev/sda5
```

You may want to get a 2nd opinion on that.

---

### Post by chkneater on 2011-04-18
The above sounds like a solid way to fix it, although I was thinking of going the route of editing the grub at startup.  Just hit e when the grub screen comes up and change the boot partition to sda5.  One of these two ways should work for sure.  

I would try my way first because you could at least restart and edit it back to normal and then try the other way up above.

---

### Post by chkneater on 2011-04-18
Also, I'm not sure what you mean that you setup the second partition with the .iso?  Does that mean you installed the OS from the ISO already or did you just copy it to that partition?

---

### Post by GregoryMA on 2011-04-18
Thanks a lot.  I will try editing grub at startup to begin and then move on.  I put the iso in the sda5.  Is that sufficient or do I need to do something else?

Greg

---

### Post by drs305 on 2011-04-18
Are you just trying to boot an ISO without actually installing it? If you have a working Grub2 installation, you can just add a menuentry for the sda5 ISO. 

The ISO file has to be constructed to allow it to be booted from Grub2, but many of the current linux distros do.

You could add the menuentry to /etc/grub.d/40_custom, below the existing lines. Save the file then update-grub.

There are two links in my signature line that might help. I am still not sure if you want to just boot the ISO and use it or if you want to install an OS off the ISO.

The second half of the "ISO Install" link in my signature line tells how to actually install an Ubuntu OS from an ISO file. The other ISO link shows many examples of grub menuentries.

---

### Post by GregoryMA on 2011-04-19
I managed to edit grub at startup to get it to load from the second partition.  It didn't boot from the iso but that is because I just had it sitting in the second partition.  

drs305, I am trying to install the iso.  I looked at your "ISO-Install" how-to.  I think this will probably work.  I just haven't had the chance to try it out yet.

---

