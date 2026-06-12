---
title: "Can't run Ubuntu.. For some weird reason"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by Landser on 2006-03-07
Hello,

First, I'm new to the Linux world and I'm trying to test Ubuntu
from the live CD.. The boot process works good so far, and then I press
enter to use the normal live configuration.. The setup program tells me
that he's decompressing files and loading Linux and then restarts the computer,
but I just get the Ubuntu boot menu again :( ...

My current OS is Windows XP SP2, and I already have an empty 5 GB
FAT32 partition for Ubuntu's use.

Any help would be appreciated.

---

### Post by christhemonkey on 2006-03-07
If your using the live CD then having spare space on your hard drive is irrelevant, is it not? As it runs on just your RAM.
Why does the computer restart? i dont remember mine doing that with the live CD....?!

---

### Post by WelterPelter on 2006-03-07
It shouldn't be restarting the computer. How far do you get into the loading before it restarts?

---

### Post by Landser on 2006-03-07
Well.. I actually meant I have the extra partition to use with Ubuntu..
So I could access the files I need from both Ubuntu and Windows,
Since the other partitions are NTFS partitions..

I boot it normally, I just set the default boot drive to be the CD-drive in the BIOS..
And I tried to do it manually with the boot menu too, but I just get the same
result!

---

### Post by sterilegenie on 2006-03-07
[QUOTE=Landser]Hello,

First, I'm new to the Linux world and I'm trying to test Ubuntu
from the live CD.. The boot process works good so far, and then I press
enter to use the normal live configuration.. The setup program tells me
that he's decompressing files and loading Linux and then restarts the computer,
but I just get the Ubuntu boot menu again :( ...

My current OS is Windows XP SP2, and I already have an empty 5 GB
FAT32 partition for Ubuntu's use.

Any help would be appreciated.[/QUOTE]

I also have the same issue as you and was wondering what type of hardware your running. I have a compaq presario sr1603wm.

---

### Post by codejunkie on 2006-03-07
for the live cd enter
```
live acpi=off
```for the install cd enter 
```
linux acpi=off
```for the cd boot command and it should work just fine.

---

### Post by Landser on 2006-03-08
> for the live cd enter
Code:

live acpi=off

for the install cd enter
Code:

linux acpi=off



Tried that, still no luck..

I have an HP machine with 512MB RAM and an ASUS Motherboard..
I'm experiencing this with Ubuntu, other live/bootable CDs work
fine..

---

