---
title: "install dualboot windows after ubuntu?"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by grimmson on 2006-07-11
Hello all. Had a mother board die and installed ubuntu to retrieve files from hdd with a new board. I've been playing with 6.06, have all the updates and I'd rather not install windows then reinstall ubuntu. The old xp install sits on /dev/hda1. Hda2 is a 5 gig ext3 space and 6.06 is on hda3. Grub properly identifies the xp partition as bootable (but with the new board it will probably crash.) can I install windows 2000 on hda1 (my son played frisbee with the xp disk) and reinstall grub to save the time of reinstalling 6.06?

small snapshot of menu.1st

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Could I print screen to have a referance for all drives and info? Any tips greatly appriciated.

---

### Post by reacocard on 2006-07-11
i think the ubuntu alternate install cd has an option to restore grub if it gets corrupted or overwritten.

---

### Post by grimmson on 2006-07-26
Didn't even have to restore the grub. Wow. Thought installing 2000 after ubuntu would replace grub. Not the first time linux has suprised me.

---

