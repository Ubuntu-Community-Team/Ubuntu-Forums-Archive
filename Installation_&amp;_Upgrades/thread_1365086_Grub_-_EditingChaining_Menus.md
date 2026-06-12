---
title: "Grub - Editing/Chaining Menus"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Mad-Halfling on 2009-12-26
Hi folks, I have an eee that came with XP so I installed eeebuntu on it and it duel booted fine.  I've now put moblin on there and it's loaded it's own grub, but I want to either combine the 2 or get the new grub to call the old one (if I can).  My eeebuntu is on hd0,6 - can I call that partition from the moblin grub and get it to invoke the grub menu on that partition?

---

### Post by oldfred on 2009-12-26
You have to install grub to that partition in the PBR. Grub2 does not like to be installed in the PBR but grub legacy works ok. adjust commands below for your partition.

#reset grub legacy boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)
# Or
6. Type "[COLOR=DarkRed]setup (hd0,3)". This is key.[/COLOR] Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
quit

Then you can add a chainboot entry - adjust drive, partition numbers:
title       Ubuntu 9.10 Karmic alpha/beta @ sdc7
root        (hd[COLOR=DarkRed]2,6[/COLOR])
chainloader +1

---

### Post by Mad-Halfling on 2009-12-27
Thanks, that got me sorted out. A few pointers for people doing this - it's easy, even if you want to install moblin last.  You may need to type "sudo /sbin/grub" rather than just "sudo grub" in moblin.
Probably the best thing to do is to reinstate your original grub by using the find command above, then setup(hd0,5) or whatever your orig partition number is.  If you use the setup(hd0) and reboot then you may find you just get a grub prompt.  If so then you can use the "setup(hd0,5)" (again, or whatever your partition number is) then "reboot" from that prompt, and that should work.  You can then use the title/root/chainloader to set up the other grub as an additional target to get the boot working (I think in my orig tests I had the wrong partition number and hadn;t tried 5, which is why I was having problems, but I couldn't bring up gparted to check, and didn't know about the find command, otherwise I think I would have got it working myself, but it's very useful to know about the extra grub commands, and it's neater (for my booting purposes) to have it booting off my original grub first, then the moblin one if I want to boot into that.

As a general thing to netbook users, if you have a compatible (atom) it's worht giving moblin a try as it's a nice, quick-booting system if you just want to get online quickly

---

