---
title: "Kind of dual booting - Feisty, grub &quot;Error 17&quot;, etc."
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by tavaryn on 2007-06-08
Okay, I'm trying to install Feisty. The install seems to go okay, until I attempt to boot into the installed partition. I installed Feisty onto my secondary slave drive (IDE). When I attempt to boot to it (via my system's F12 boot menu) I see the text "LI_", and the cursor blinks until I turn the system off. When I attempt to boot to my primary master IDE drive (which the install shouldn't have even touched), I get grub, but before any menu is displayed, I get "Error 17".

For the record, here's my drive setup:

SATA: Windows XP partition.
Primary master IDE: NTFS file storage partition, didn't think the install would touch it at all.
Secondary slave IDE: What I tried to install Feisty to.

I've tried rebooting and installing again. Also, everything seems to work fine from the live CD (except my wireless, but that'll be a different topic altogether)

Anyone have any ideas? :/

---

### Post by benanzo on 2007-06-08
I think GRUB is confusing your partitions.  Do you have any other partitions on that secondary slave disk (where Feisty is installed to) besides those used by Feisty?

It sounds to me like GRUB installed itself to the MBR of your SATA drive.  Before we go throwing out advice which might further damage your setup, we need to know what your disk partitions are set as.

You can find this info by booting to the Feisty LiveCD and opening GParted (**System -> Administration -> GNOME Partition Editor**).Then take a screenshot (**Applications -> Accessories -> Take Screenshot** and upload it here.  Be sure to capture a picture of each of the disks in the menu in the top-right of GParted.

Or a less cumbersome way would be to open a terminal (**Applications -> Accessories -> Terminal**) and type:
```

sudo parted /dev/sda
# then at the parted prompt type:
print

```
This will list all the partitions and their relevant flags on the first SATA disk.
You can repeat these steps using */dev/hda* and */dev/hdb* for the IDE disks in place of the */dev/sda* for the SATA disk.

Paste the output of each of those here.

---

### Post by tavaryn on 2007-06-08
Here you go - sorry about the overnight delay, a few of us have to sleep every now and then. ;)

```
ubuntu@ubuntu:~$ sudo parted
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print all                                                        

Disk /dev/sda: 82.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  82.3GB  82.3GB  primary  ntfs              



Disk /dev/sdb: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  38.3GB  38.3GB  primary   ext3         boot 
 2      38.3GB  40.0GB  1686MB  extended                    
 5      38.3GB  40.0GB  1686MB  logical   linux-swap        



Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  120GB  120GB  primary  ntfs         boot 



```

I assume "print all" was just as good as printing them all seperately - as far as I can tell, it gave me the same result.

sda is my primary master IDE drive (the one that gives me the grub "error 17"), sdb is my secondary slave IDE  (the one I tried to install Ubuntu to; upon boot I get "LI_" and nothing more) and sdc is my SATA drive (WinXP)

---

### Post by tavaryn on 2007-06-09
Alright, I managed to 'fix' this problem by removing both my SATA drive and my primary master IDE drive. Ubuntu installed successfully, and I can boot to it. However, when I do so, the system runs incredibly slow. It takes at least five minutes to boot, and when I finally get a mouse pointer on the screen, it moves at about 1 FPS (including the animation of the 'busy' cursor.) I think this may be a physical problem with the hard drive, but I'm not positive. I had no speed problems when running from the Live CD.  *shrug*

---

