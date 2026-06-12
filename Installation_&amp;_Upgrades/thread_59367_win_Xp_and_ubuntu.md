---
title: "win Xp and ubuntu"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by blackwind on 2005-08-23
hi, i have the ubuntu cd (the newest), and i have already installed winxp in my disk with a bunch of things i dont want to loose.
when i installed it (winxp) i didnt create a partition.
Now.... how can i install ubuntu and keep my winxp safe??

thanks

---

### Post by c0rderr0y on 2005-08-23
i use partition magic for this but make sure you dont move the windows partition just 
resize it and add the linux parition to the end.  you will mess up windows if you move the partition.

---

### Post by Chris Cromer on 2005-08-23
Before you do any type of partition work, make sure to backup. I tried partition magic and it failed and it nuked my windows xp.

Luckily I had backups though, otherwise I would have lost everything.

Because of my problems I had no choice but to completely uninstall windows to get linux.

What I did was insert my windows xp disc into my computer and started my computer. It should auto boot if your bios is set up properly. I then chose to delete all partitions that where listed when I went to install it. Then I gave windows xp about 4GB of space.

After windows xp was installed then I inserted my ubuntu install disc and started my computer. I created 3 partitions manually for linux. One for ubuntu, which was a primary bootable parition and was 4GB. One called /home so that when I reinstalled linux or windows I wouldn't lose my data since it's on another parition, it was 7GB. Then one more partition called /shareos which uses a FAT32 file system and is 3GB. This partition is a shared partition and can be access from both windows and linux. That way I can transfer files from windows to linux and vice versa.

Please note that if you install linux first you will run into problems because it will replace the master boot record with it's own boot program. So always install windows first then linux, that way you can use grub to have a dual boot system with both windows and linux chooseable at startup.

I hope some of this helps you. And I stress very seriously, make backups before you do anything with partitions.

---

### Post by blackwind on 2005-08-30
ok, thank, i'll try with the partition magic.

---

