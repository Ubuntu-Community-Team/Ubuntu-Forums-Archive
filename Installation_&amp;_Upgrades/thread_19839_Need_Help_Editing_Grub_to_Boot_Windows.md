---
title: "Need Help Editing Grub to Boot Windows"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by ryanrad on 2005-03-13
Hello everyone.  First of all, I just want to say that Ubuntu is awesome.  I've gotten frustrated with a couple other distro's, but this one is my M$ killer.  However, I've still got to use it for a little gaming.

Here's my problem:
I've got Windows and Ubuntu installed on an SATA drive.  My /home directory is on an IDE drive.  I think I screwed everything during setup and GRUB ended up on the MBR of my IDE drive.  

Ubuntu boots up like a gem, but Windows won't load.  Windows works fine if I switch the HD priority in my BIOS settings.  I've tried editing GRUB with hd1,0; hd1,1 and a couple others with no luck.  I thought one of these should work since Ubuntu is on the same drive, hd1.

Here's my current GRUB configuration:
title		Ubuntu, kernel 2.6.10-4-amd64-generic Default 
root		(hd1,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-4-amd64-generic Default (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-4-amd64-generic 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.10-4-amd64-generic root=/dev/sda3 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.10-4-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-4-amd64-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.10-4-amd64-generic root=/dev/sda3 ro console=tty0 single
initrd		/boot/initrd.img-2.6.10-4-amd64-generic
savedefault
boot

title		Microsoft Windows XP Home Edition
root		(hd1,1)
savedefault
makeactive
chainloader	+1

Any suggestions, or should I simply reinstall to my SATA and move /home post install?

---

### Post by Buffalo Soldier on 2005-03-28
What's the output of **sudo fdisk -l**?

---

### Post by panabar on 2005-04-03
I have nearly the same problem. I installed windows a sata harddrive, then I installed ubuntu on on the third partition of my first hdd. Now I'm trying to edit grub so I can boot into windows without changing bios setup (Switching boot priority to sata boots into windows).

output of 
sudo fdisk -l  gives

```


Disk /dev/hda: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1      310097   156288856+  55  EZ-Drive

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      143055    72099688+   7  HPFS/NTFS
/dev/hdb2          143056      145186     1074024   83  Linux
/dev/hdb3   *      145187      154874     4882752   83  Linux
/dev/hdb4          154875      158816     1986768   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

```

I want to boot from sda1. 

I've tried adding this drive to grub as ( guessing: hda1 is hd0,0 sda1 could be sd0,0 )
```

 title          Windows XP
 root           (sd0,0)
 makeactive
 chainloader    +1

```

Thank You.

(This is my desktop system - Asus A7N8X - Deluxe with Nvidia 2 Ultra )

---

