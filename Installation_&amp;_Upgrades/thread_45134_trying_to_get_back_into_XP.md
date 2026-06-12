---
title: "trying to get back into XP"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by brendan on 2005-06-28
Hi i'm running XP, thought I would try out Hoary, I used partition magic, it gave me 2 partitions, ext and swap .  then I installed hoary, I guess I dosed off not paying attention to the install, but now I can not access XP, any one have any thoughts. looking forward to your help. thanks

---

### Post by art on 2005-06-28
If you get an error like I was getting, about xmnt2002, look here

[http://supportforum.sun.com/sjds/index.php?t=msg&goto=2762&rid=0](http://supportforum.sun.com/sjds/index.php?t=msg&goto=2762&rid=0)

That was the trick for me. 
HTH

---

### Post by brendan on 2005-06-29
thanks art.
I would try what you recommended, but where does all this get type into, theres terminal, terminal root, i just found grub before it boots just hit esc.  I really don't care about the getting into XP its just I have fotos on Xp of my sons first computer he built.  I did use terminal root and type in fdisk it  shows
hda1 boot, primary, linux, ext, 3
hda5 nc, logical, linux, swap / solaris
not sure if this helps any one, to be able to help me.  I'm sure XP is on the hda0, just need help on how and where to type the info so i can get back into XP again thanks all for everyones help

---

### Post by SQFreak on 2005-06-30
[QUOTE=brendan]
hda1 boot, primary, linux, ext, 3
hda5 nc, logical, linux, swap / solaris
not sure if this helps any one, to be able to help me.  I'm sure XP is on the hda0, just need help on how and where to type the info so i can get back into XP again thanks all for everyones help[/QUOTE]

I'm a little confused. Could you paste the output of < sudo fdisk -l /dev/hda > please? I didn't think an hda0 was possible...

My hard disk still has a Dell utility partition on it (I just PartitionMagic'd since I wanted to dual boot), which is hidden entirely from Windows (and linux for the most part), but fdisk still identifies it as /dev/hda1 and has /dev/hda2 (HPFS/NTFS which is WinXP) as the Boot partition. (GRUB is in the MBR and I use it.)

---

### Post by art on 2005-06-30
You need to edit the /boot/grub/menu.lst file, as for example, type in the teminal

sudo gedit /boot/grub/menu.lst , and at the end of this file find entries for windows. Make it look like the following:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
unhide (hd0,0)
root            (hd0,0)
makeactive
chainloader     +1

Hope this will work.

---

