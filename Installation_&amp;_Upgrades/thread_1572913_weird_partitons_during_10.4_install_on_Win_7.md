---
title: "weird partitons during 10.4 install on Win 7"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by imipolex-G on 2010-09-11
Trying to install 10.4 side by side on a Win 7 laptop disk, but Ubuntu install seems to have problems seeing the correct partitions (though it seems them correctly when booted on a USB drive on the same machine). During installation, Ubuntu comes up with nonsensical partition sizes for sda3 and sda4, so it seems a dangerous idea to go ahead with any partitioning. (Along with this, no side by side option appears.) I am thinking Ubuntu install has trouble with "dynamic"Win 7 disk.

This, BTW, even after going so far as to format the partitions as Linux EXT4 and swap, and labelling them appropriately. None of this is seen by the installer, only by the booted USB Ubuntu. Any ideas? It does look like a bug unique to the install process.

---

### Post by thegod_slayer on 2010-09-11
first of all don't try the side by side option. allways go for specify partitions manually.
next ubuntu can't revert or change ntfs partitions so delete those partitions to free space, then 
make your swap and /.
another thing go for ext3 partition in /
as ext3 is identified by win and so makes it easy to format with win.
the left over space can me made into fat32 so that both linux as well as win can access it.

---

### Post by wilee-nilee on 2010-09-12
> **imipolex-G said:**
> Trying to install 10.4 side by side on a Win 7 laptop disk, but Ubuntu install seems to have problems seeing the correct partitions (though it seems them correctly when booted on a USB drive on the same machine). During installation, Ubuntu comes up with nonsensical partition sizes for sda3 and sda4, so it seems a dangerous idea to go ahead with any partitioning. (Along with this, no side by side option appears.) I am thinking Ubuntu install has trouble with "dynamic"Win 7 disk.

This, BTW, even after going so far as to format the partitions as Linux EXT4 and swap, and labelling them appropriately. None of this is seen by the installer, only by the booted USB Ubuntu. Any ideas? It does look like a bug unique to the install process.

Post a screen shot of gparted from the Ubuntu live cd.

---

### Post by imipolex-G on 2010-09-15
Screen shot from a USB-drive boot (saner, correct):

[IMG]http://img198.imageshack.us/img198/2511/screenshotusbboot.png[/IMG]


Screen shot of Live CD/install process (wrong, not sane)

[IMG]http://img215.imageshack.us/img215/7756/screenshotlivecd.png[/IMG]

---

### Post by imipolex-G on 2010-09-17
The problem appears to be the Windows 7 "dynamic disk" (LVM, MS-proprietary style), as suspected. Linux can interpret the logical partitions in some modes, but cannot do much of anything with them (since they are MS logical volumes, not real partitions). 

I have decided that, since the Win 7 disk is useful for some things, and I really do not want to recreate it from scratch, I am buying another laptop disk and installing Ubuntu as the primary (with an XP partition for Windows stuff). Seems to be the easiest route. I spspect the Win 7 disk will spend most of its lifetime gathering dust.

But overall, MS "dynamic disk" would seem to be a major problem for non-MS OSes.

---

