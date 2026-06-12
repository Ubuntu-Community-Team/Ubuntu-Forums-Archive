---
title: "GRUB Troubles"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by ba5e on 2005-03-02
I am basically unable to boot Windows xp, this is what happened:

installed winxp on h :?: da1 (primary, NTFS)
then installed Ubuntu on hda2(Primary, EXT3) with swap hda5 (logical) 

both os's woring fine :)
made a backup (with norton Ghost) of hda1

then i deleted hda1 (left hda2&5 alone), recreated empty hda1 partition and restored a winxp backup with ghost, winxp works fine.

here is where it gets tricky: I read that it is easy to reinstall GRUB, so I:
booted ubuntu live cd
mkdir /mnt/root
mount /dev/hda2 /mnt/root
chroot /mnt/root
grub-install /dev/hda1

(device.map)
(hd0)	/dev/hda
(hd1)	/dev/hdg
(hd2)	/dev/hdh

(relevant menu.lst) (btw this has not changed since it worked when both os's were on before)

title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

 :?: 
Loading linux works fine, but this menu item (Windows XP) just takes me straight back to GRUB (no errors etc etc)
 :?: 
so WHAT is going oN!?!? help appreciated.

---

### Post by alastair on 2005-03-02
"grub-install /dev/hda1"

I think that should have been :

grub-install /dev/hda

You have to be brave, or foolish, to play around like this!

---

