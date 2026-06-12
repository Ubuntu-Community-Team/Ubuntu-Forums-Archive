---
title: "Grub Error When Adding/removing Drives"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by slaskehage on 2007-12-13
**Here's the deal :**

pri master no drive
pri slave no drive

sec master cdrom
sec slave dvdrom

pri sata holds xp (ntfs)
sec sata holds swap and / (ext3)

*I installed xp to pri sata and ubuntu to sec sata - thats all good*

**UNTIL :**

*I plug a couple of old drives to the pri master/slave channels*

**THEN **

**GRUB ERROR 22**

Anybody knows how to fix this issue ?
I tried fixing MBR and stuff - but the only htinx that really works for me is an ubuntu 6.06 desktop cd - it allows me to rescue broken system and takes me through the installer as usual - but seems to only install the grub again - just dont want to go all that way to fix something simple as this probably is..

OOhh by the way Grub is located at (hd0) that much I remember - and that disk is still intact - but maybe another disk is now hd0 - why cant grub sort of auto update drives ??

Thanx in advance!

---

### Post by froy02 on 2007-12-13
When you intstalled HD's on your ide connectors all the hardrive numbering changed big time.  The ide' drives would be numbered first so now all the list of drives in your /etc/boot/grub .menu.lst are off.  
You need to post the result of 'sudo fdisk -l and a copy of your menu.lst.  We need that info.

I think if you remove the drives you hooked up. You get back to your original installation.

---

### Post by logos34 on 2007-12-13
like froy02 says fdisk and menu.lst will fill us in.  You'll obviously have to boot frm the ubuntu live cd for that.  But from your description I'm guessing that grub is probably on the mbr of the windows drive pointing to root at (hd1,1).  Adding two ide drives pushed it from second to fourth place.  So you could try booting to the grub menu screen and on the ubuntu kernel hit 'e' to edit, 'e' again on the 'root' line and change to (hd**[COLOR="Red"]3[/COLOR]**,1) or (hd3,0) if it's the first partition, ahead of swap.  Hit 'b' to boot.  If it works make the change permanent by editing menu.lst

---

### Post by slaskehage on 2007-12-14
I learned way back that removing the newly inserted disks would fix the problem

But it is really rather a workaround for the problem - I need these two disks.

(same problem occurred in a different setup - when removing my sec sata holding the linux files- the grub on pri sata with the xp files came with the same error - how can that be possible ?  - grub should just select the bootable partition rather than breaking down over something missing.) 

enough complaints..

I tried a reinstall 8.10 but it installer when finished apparently did not put the grub on hd0 (dont know why)..

The grub 22 keep comming up even after 8.10 and 7.10 re-install - pretty crappy

Furthermore my raptor holding my xp partition is 30/37gb full and takes like 5-10minutes for the partition manager to 'find' this does not occur when drive is empty - mostly movies on it. pretty wierd and even more annoying ..

Will post the : sudo fdisk -l later on - if I get it to work or not..

Best regard and thanx in advance..

---

