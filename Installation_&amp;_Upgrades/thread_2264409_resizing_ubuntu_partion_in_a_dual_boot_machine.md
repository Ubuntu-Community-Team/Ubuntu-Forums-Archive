---
title: "resizing ubuntu partion in a dual boot machine"
date: 2015-02-07
forum: Installation &amp; Upgrades
---

### Post by bengaltiger2 on 2015-02-07
Hi,

I have a dual boot machine with Win8 and Ubuntu.
I want to reduce Win8 partition and increase ubuntu partition.
I can reduce win8 partition.

See the attached partition info.
Need help, how I can increase ubuntu partition and reconfigure grub.

more info about the system

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

Thanks,
BT[ATTACH=CONFIG]259786[/ATTACH]

---

### Post by Mark Phelps on 2015-02-07
HOW did you shrink sda2? It doesn't look good in the screenshot.  You should reboot into Win8 to insure it still works before proceeding any farther.

---

### Post by Bucky Ball on 2015-02-07
> **Mark Phelps said:**
> HOW did you shrink sda2? It doesn't look good in the screenshot.  You should reboot into Win8 to insure it still works before proceeding any farther.

Agreed. Best fix that exclaimation mark in your Gparted screenshot first. 

Welcome to the forums. You also have this in your Boot Info Summary:

```
=> Windows is installed in the MBR of /dev/sdb.
```

A bit confusing, as there is no /dev/sdb in your output.

PS: Please use [code] tags for output. Easier to read. See the last link in my signature for how. ;)

---

### Post by bengaltiger2 on 2015-02-08
thanks for the reply.
Yes I will shrink windows 8 partition from windows, there is a tool for it.
one bottable usb drive was there thats the reason boot info prints this.

I get some info about how to resize ubuntu partition.
Now after that how I can fix grub , so it can work like before (boot menu gives me both ubuntu and win options)

BT

---

### Post by Bucky Ball on 2015-02-08
To fix grub, Boot Repair is your friend. Have a look at these two links. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

To resize Ubuntu partition, you need to boot from the install media, 'Try Ubuntu' and use Gparted. After that, Boot Repair. BRepair can produce a lot of information about your setup. Keep a record of the boot info file it creates in case it doesn't work and you need to post that info here. ;)

---

