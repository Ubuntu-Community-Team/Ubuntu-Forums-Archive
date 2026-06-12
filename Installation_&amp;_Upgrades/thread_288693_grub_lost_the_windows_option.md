---
title: "grub lost the windows option"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by the bogs on 2006-10-30
I upgraded to edgy. When I restarted grub had lost the option to boot to winxp. How do i get it back?

---

### Post by Sef on 2006-10-30
Restore [GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by confused57 on 2006-10-30
> **the bogs said:**
> I upgraded to edgy. When I restarted grub had lost the option to boot to winxp. How do i get it back?

If you haven't found a solution, boot into Ubuntu, open a terminal, and post the output of:

```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition table and what Windows entry you may need in your /boot/grub/menu.lst.

---

### Post by blackest_knight on 2006-10-30
(commands are written in bold) 
ok go to 
[B]cd /boot/grub/
ls[/B]
you will see menu.lst 
if you are lucky menu.lst~
**more menu.lst~**
scroll down has it got your windows boot option ?
if so you can do this 
[B]sudo cp menu.lst menulst.old
sudo cp menu.lst~ menu.lst
[/B]
that will restore the backup

no good?
ok you need to edit the menu.lst file do you know the order of your partitions ?

below is an example. with xp and osx entrys 
[B]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		OSX 86 10.4.5
root		(hd0,1)
savedefault
makeactive
chainloader	+1

[/B]
these are a couple of menu entrys for non linux operating systems 

very important is the line starting root (hd0,x)
this hard drive has 3 partitions xp, osx , ubuntu
the first xp is at     hd0,0
the second osx is at   hd0,1
the third ubuntu is at hd0,2

if you had a second hard drive with xp on the first or only partition 
then it would be root (hd1,0)

**sudo nano /boot/grub/menu.lst**

or 

**sudo gedit /boot/grub/menu.lst**

and add the necessary entry nano is great if you havent got a desktop and just a command prompt. 

you probably are best to copy and paste the non linux section of your old menu.lst into the one edgy created. probably a new linux entry in the edgy one

---

