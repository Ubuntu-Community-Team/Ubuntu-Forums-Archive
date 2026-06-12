---
title: "Installed Windows after Ubuntu, restored Grub, but missing a grub entry for Windows"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2008-03-20
I need to add a Windows entry to my menu.lst file.  I recently installed XP on an already existant NTFS partition that's on the same hard drive as Ubuntu (one single hard drive here).  Windows installed perfectly fine.  My next task was to restore GRUB, using a Live CD.  That worked.  Except, that grub didn't autodetect Windows and add it to the menu.lst file when it restored grub.  I thought it was suppose to, but then again, I've never done this before.

So what should I do to get a new entry in there so I can boot to Windows if I wish upon boot?

---

### Post by Herman on 2008-03-20
Ubuntu automatically detects Windows when you install Ubuntu and there is a previoulsy existing Windows in the hard disk, but GRUB doesn't do that when you re-install GRUB.

You can easily add a Windows entry to the bottom of your /boot/grub/menu.lst file though, by copying an entry for it and pasting it there.

You can copy this entry and paste it to the bottom of your /boot/grub/menu.lst for example,
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```It might not boot because I'm not sure what partition number you have Windows in.
You'll need to edit it with the right partition number.
Take a look with the command 'sudo fdisk -lu', or with GParted or some other partition editor to see what partition number it is.

Here's a conversion table to change it to GRUB's numbering system,  [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").

Or post a copy of 'sudo fdisk -lu' here for help.

Regards, Herman :)

---

### Post by deltaprime on 2008-03-20
couldnt say it any better way! good job

---

### Post by diablo75 on 2008-03-20
Here's what I got:

```
zeke@zeke-laptop:~$ sudo fdisk -lu
[sudo] password for zeke:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x994a994a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    89048294    44524116   83  Linux
/dev/sda2        89048295    92952089     1951897+   5  Extended
/dev/sda3   *    92952090   117210239    12129075    7  HPFS/NTFS
/dev/sda5        89048358    92952089     1951866   82  Linux swap / Solaris
zeke@zeke-laptop:~$ 

```

Thanks for your help!  :)

So what do I do next?

---

### Post by Herman on 2008-03-20
:) Okay diablo75, it looks like your Windows XP is in partition number 3, /dev/sda3 in Linuxese, that converts to (hd0,2) in GRUB language.
```
# This entry was added by zeke for a non-linux OS
# on /dev/sda3
title        Microsoft Windows XP Home Edition
root        (hd0,2)
savedefault
makeactive
chainloader    +1
```
Try that and it should work.
Feel free to change the words after the word 'title' with anything you like too, if those don't describe your Windows XP version.

Regards, Herman :)

---

