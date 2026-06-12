---
title: "Grub Error 22 &amp; 13 in dualboot."
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by t. arcane on 2008-05-20
Hey there. I'm having a little problem, which it seems that I'm unable to solve un my own.

I recently installed Ubuntu 8.04 64bit on a harddrive containing Opensuse10.3. This appeared to have messed with my grub preferences.

Now my harddrive lookes something like this;

80 GB IDE 
-1 Gb LinuxSwap partition
-12 Gb ext3 mountpoint /
-3 Gb ext3 mountpoint /home
- 60 Gb fat32 mountpoint /windows

250 GB SATA
All with Windows Vista.

The error that i get when trying to boot Vista;
"Error 13; invalid or unsuported format"

When trying Ubuntu;
"Error 22; No such partition"

/boot/grub/menu.lst says

for Ubuntu;

root (hd0,1)
kernel /boot/vmlinuz-2.6.24blabla 
initrd /boot/intird.img-1.6blabla
quiet

for Win;

root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Can't seem to figure in what order grub has assigned the different drives.

Can anybody help or direct me to a solution?

---

### Post by dstew on 2008-05-20
From the error messages, it might just be that the BIOS drive order is coming up with the SATA as drive 0, and the IDE as drive 1. You could check real quick by pressing 'e' at the grub menu and editing the root statments to try the other drive order. That is, try root (hd1,1) for Ubuntu, and (hd0,0) for Windows (you might also have to remove the map statements). If it works, then you can change it permanently by editing /boot/grub/menu.lst.

---

### Post by t. arcane on 2008-05-20
Thanx - that worked.

However, I solved the problem in the same way myself. Sorry, but thought that I had tried that option already ;-)

---

