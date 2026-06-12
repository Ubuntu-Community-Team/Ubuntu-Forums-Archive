---
title: "Boot CD"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by Mirth on 2005-06-28
I installed Ubuntu fine and as is usually the case with most people I know that have dual booted with WinXP Home the GRUB AND LILO Boot failed in the installation but everything else was fine.  Is there some way to make it so I can boot from a CD?  That's what I did to get to the Ubuntu installation..

Help! D:

---

### Post by mingus on 2005-06-28
Can you still boot Windows OK?  Are you seeing grub at all, if so, what?  Did you try to install LILO, too?  Do you know how to get into Ubuntu without grub?  Do you have a Live-CD?  Can you describe your disk layout and partitioning?

Not to worry.  The questions just give us an idea of what to point you to . . .

---

### Post by Mirth on 2005-06-28
I still boot Windows fine.  I don't see GRUB at all, and I couldn't successfully install it.  I do have a live CD and I have tried installing LILO.  I don't know how to get to Ubuntu without GRUB.  My disk layout is

One Hard-Drive:
C:\ is a 50 GB Partition that contains Windows
G:\ is a 25 GB Partition that contains Ubuntu
There's also this random 32MB partition that's formatted to windows and I'm sure it's for something but I'm not sure.

---

### Post by mingus on 2005-06-28
[QUOTE=Mirth]
One Hard-Drive:
C:\ is a 50 GB Partition that contains Windows
G:\ is a 25 GB Partition that contains Ubuntu
There's also this random 32MB partition that's formatted to windows and I'm sure it's for something but I'm not sure.[/QUOTE]

You're right, it is something - probably a recovery partition, and you have either a menu choice or a CD which can restore your system from it?  That you don't see it suggests that it is "hidden", and this could be why the boot loader won't install.  (BTW, installing another W$ to dual-boot would have the same problem.)

Also, re Ubuntu being on "G" - W$ assigned this partition a driver letter???  Before you installed Ubuntu?  Do you still see "G" in Windows Explorer?  Go to My Computer/Manage/Disk Manager and what do you see?  Also does DM show the recovery partition?

To get grub set up, we need to see how the disk is really laid out and what grub thinks it is.  So, boot from the Live-CD.  When you get into Gnome, go to Applications/System Tools/Root Terminal and at the prompt do:
#fdisk -l
the partition table will be displayed, pls post that back here

This next step may seem a bit complicated, but it's not really.  From the fdisk display, do you know which partition holds root (/)?  If you do not, then try:
#cfdisk
The partition table will be displayed again but with a "label" column which will show the mount points inside brackets, look for [/] and [boot] (boot may not be there, that's OK).

When you have determined which partition / is on, then at the prompt do:
#mount /dev/hdaX /media (where X is the partition number, e.g., hda3)
if there is also a boot partition, then do
#mount /dev/hdaX /media/boot (Where X is the number of the boot partition)
now do this:
#cd /media/boot/grub
#cat menu.lst
post that display back here and
#cat device.map
post that display back here, too

now we'll have the info we need to properly set up grub and dual-boot Windows

---

### Post by Mirth on 2005-06-28
I'll try that and I'll get back to you.  Hope this works :3

---

### Post by mingus on 2005-06-28
[QUOTE=Mirth]Hope this works :3[/QUOTE]

No reason that it shouldn't, although with a hidden partition, it may take some tweaking.

---

