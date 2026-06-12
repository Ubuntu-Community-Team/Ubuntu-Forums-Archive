---
title: "HDD problems."
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by gcauson on 2010-02-10
I have two hard drives installed, the first with XP, and I wanted to install Ubuntu on the second. I did a low level format on the hard drive to wipe it clean and then booted the Ubuntu disk, when going through the installer it does not find the hard drive I want to use just the one with XP, and also when on XP it doesn't  find the drive either. The bios however does find the drive.

Any help with this problem would be great.

---

### Post by johnson.d on 2010-02-12
You can perform the following steps to check whether the disk, which is Formatted in low level, is detected by Ubuntu.
1) Boot the system using Ubuntu live cd
2) In the initial menu select the first option (Try Ubuntu without any change to your computer)
3) After the desktop has loaded you can goto Applications -> Accessories -> Terminal
4) You can use cfdisk at the terminal to create the partition in the drive you have done a low level format.
5) After creating the partitions reboot the system and install Ubuntu

---

### Post by gcauson on 2010-02-12
I did what you said johnson.d but I only get as far as running cfdisk becaue when I run it, it just says "FATAL ERROR: Cannot open disk drive, press any key to exit cfdisk"
__

---

### Post by lavinog on 2010-02-12
instead of using cfdisk, try gparted: press alt-f2 then type: gksu gparted
On the upper right of the window there should be a drop down to select what drive you want to manipulate.  When you select the second drive (most likely /dev/sdb) it should ask you if you want to create a msdos partition table.

---

### Post by gcauson on 2010-02-12
gparted only picks up the first drive that has xp on and i dont want to change, and doesnt seem to find the second one, which is the one I want it to.

---

### Post by lavinog on 2010-02-12
How did you perform the "low-level format"?

you should post your /var/log/messages.
you can use system>administration>log file viewer to copy and paste the log on to here, but make sure you use code blocks to make it easier to read.

---

### Post by johnson.d on 2010-02-12
After you open Gparted it shows only the first hard-drive by default. In order to show the second one you have to use the drop down, that is displaying /dev/sda. It might be showing the second hard-disk as another option probably you have to select that and proceed further.
If this doesn't work you can probably use the following commands to check whether the harddisk is detected by Ubuntu:

```
$ hdparm -I /dev/sdb
```
If your second hard-drive is named sdb in Ubuntu

```
$ lshw -c disk
```

You can probably post the output of the above commands.

---

### Post by gcauson on 2010-02-17
I tried that code and it just said I don't have permission.

But in the disk utility it seems to show both my drives, so using this I tried to create the master boot record on the drive I want it, but it just came up with this error message, 

"Error creating partition table: helper exited with exit code 1: cannot open device: read-only file system"

---

### Post by johnson.d on 2010-02-23
You can run both the commands as sudo user ie
$ sudo hdparm -I /dev/sdb
$ sudo lshw -c disk

---

