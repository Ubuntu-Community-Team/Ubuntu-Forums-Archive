---
title: "Can not sync the partitions in rEFIt--Suspect there was an error with installation"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by AshToTheLeigh on 2010-09-27
Please bear with me as I'm incredibly new to Linux and shell scripting and all that good stuff. This will be a fairly lengthy post, as I don't really know which information is pertinent to the problem at hand and which is irrelevant. 

I installed Ubuntu on my Macbook following the instructions on this page: [http://www.maclife.com/article/howtos/install_linux_your_mac](http://www.maclife.com/article/howtos/install_linux_your_mac)

At step 7, /dev/sda3 was not in the dropdown menu of options, so I picked...I can't remember. Either /dev/sda or /dev/sda2. I think this may be the beginning of the root of my problems.

Step 8 is where it all falls apart. I get the following error message:
"Status: MBR partition table is invalid, partitions overlap.
Status: GPT partition of type 'Unknown' found, will not touch this disk."

Sooo since I can't sync the partitions, I can't get Linux to load unless I'm loading it from the LiveCD.

I've tried steps 1-10 on this page:
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

However, under step 4, I could either "Save" the file randomly, without actually saving it to /mnt/root, or I could just open it and run the installer. I think I went into FF preferences and changed it to let me pick where each download would be saved, but when I actually clicked on the download link and then "Save", after finding the folder and clicking the final button (Which I think actually said "Open" instead of "Save"), nothing happened. I tried running the rest of the steps after just opening the installer on its own, but of course just got error messages. I hate not being able to troubleshoot this on my own!

Thank you in advance for any help you can provide!

---

### Post by srs5694 on 2010-09-27
The usual instructions for dual-booting OS X and Linux on a Mac involve using a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is a flaky and dangerous hack. Unfortunately, there also seems to be a bug in some versions of the tools that the Web-based guides suggest using, resulting in problems like the on you're experiencing.

Chances are you can fix the hybrid MBR using Linux fdisk or [GPT fdisk (gdisk);](http://www.rodsbooks.com/gdisk) however, if you need exact instructions, you'll have to post the contents of your MBR partition table. Boot your Ubuntu CD, open a text-mode shell, and type "sudo fdisk -l". Post the results between a [noparse]```
[/noparse] and a [noparse]
```[/noparse] string. Information on the GPT partitions could also be handy; type "sudo apt-get install gdisk" and then, when that's done, type "sudo gdisk -l /dev/sda" and post the output, also between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings.

---

### Post by AshToTheLeigh on 2010-10-03
Thank you for your quick response! I'm sorry my response was not quite as prompt :-/

sudo fdisk -l produced the following: 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007cfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       12819   102760448   af  HFS / HFS+
/dev/sda3               1       12819   102967295+  ee  GPT
/dev/sda4           12819       19181    51098624   83  Linux

Partition table entries are not in disk order
```

and 

sudo apt-get install gdisk gave me:

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gdisk
```

and then sudo gdisk -l /dev/sda ended up with:

```
sudo: gdisk: command not found
```.

Anyway, if you couldn't already guess, I will need exact instructions on how to fix this. Thank you in advance for your time!!

---

### Post by srs5694 on 2010-10-03
If you're only dual-booting Linux and OS X (no Windows), then you can fix it by deleting MBR partition #3:


[LIST=1]
[*]Boot a Linux emergency CD or the Ubuntu live CD.
[*]Open a text-mode shell (terminal) window.
[*]Type "sudo fdisk /dev/sda".
[*]Type "d" and select partition #3.
[*]Type "p" and verify that you've got partition #1 (Type "ee"), partition #2 (type "af"), and partition #4 (type "83"). If not, type "q" to exit and start again.
[*]Type "w" to save your changes.
[/LIST]


If you're also booting Windows, you'll need to create a fresh hybrid MBR. Post back if this is the case and I can provide more complete instructions.

---

### Post by AshToTheLeigh on 2010-10-03
This worked perfectly!!! Thank you :-D

---

