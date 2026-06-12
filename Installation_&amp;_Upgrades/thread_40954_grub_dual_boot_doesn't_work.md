---
title: "grub dual boot doesn't work"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by robroy on 2005-06-11
I have a system with win 2k on one hd and just installed ubuntu on the other, now when I reboot the comp stops at the grub loading. the only keys that will work are ctrl,alt.del
Tried reinstalling ubuntu, tried the repair/reinstall that I saw in another post but the comp didn't recognise the Do: command. Any help appreciated

---

### Post by defkewl on 2005-06-11
Could you please copy-paste your /etc/fstab and /boot/grub/menu.lst here?

---

### Post by robroy on 2005-06-12
can't get in to either hd to get anything

---

### Post by Dogmeat on 2005-06-12
Get your XP disk, go to Repair console and type fixmbr. You should at least be able to go back to XP, and use a ext2/ext3 viewing filesystem to check out your menu.lst. This happened to me some time ago, since then I burned myself a RIP boot cd (its a minimal linux system for recovery in problems like these, its a 26mb iso IIRC) so if you for some reason cant get your XP cd I recommend you get RIP (do a google search for RIP linux)

---

### Post by pablokal on 2005-06-12
[QUOTE=Dogmeat]Get your XP disk, go to Repair console and type fixmbr. You should at least be able to go back to XP, and use a ext2/ext3 viewing filesystem to check out your menu.lst. This happened to me some time ago, since then I burned myself a RIP boot cd (its a minimal linux system for recovery in problems like these, its a 26mb iso IIRC) so if you for some reason cant get your XP cd I recommend you get RIP (do a google search for RIP linux)[/QUOTE]
I recently tried a dual boot and as grub refused to install, i installed Lilo; i wa able to use Ubuntu but as xp nothing ever happened after that;
also fix mbr didn't work anymore; i tried to find answers in all kind of forums but nothing worked as predicted; the only solution was to delete the linux ext3 and swap partition with the partition tool from the Repair console from Xp; after that a reinstall from the xp cd and after that i could set back a powerquest image back; even then my d partition with all personal and working data was not allright; the partition allocation table was fucked up; i was able to repair that with ' fixboot D:\
"  command in the repair console; it took me two days to  find the right solution and don't dare to try another dual boot system again.

---

### Post by robroy on 2005-06-12
Don't have xp, I am running 2000 pro. I have another system that is dual boot, win 2k and iccaros linux that works without any problems. I had heard good things about ubuntu, tried the live cd,was happy with that but since I installed it on the slave drive nothing. Can't even get to repair it with the win2k cd in repair mode. It supposedly reinstalled some files, rebooted and froze again at the grub loader. Downloaded and burnt the rip-linux cd and will give that a try

---

### Post by Dogmeat on 2005-06-13
ok you should be able to mount your linux partitions with it, if you need more help to fix your boot let us see the /etc/fstab and /boot/grub/menu.lst files  :smile:

---

### Post by robroy on 2005-06-13
Given up, I'm reformatting and reloading both drives. Will let you know if it works next time
Thanks everyone for help

---

