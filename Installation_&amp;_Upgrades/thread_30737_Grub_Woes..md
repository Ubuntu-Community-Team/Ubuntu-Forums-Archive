---
title: "Grub Woes."
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by bakagamer on 2005-04-30
Recently, I've been trying to install Ubuntu on my old computer. Needless to say it isn't working.  :smile:  Apparently the Base system installs without a hitch, but when it tells me to reboot, I do and...

Grub>

Frankly, I don't know how to use the grub shell. 

I'm running a Pentium 2 that's about 400mhz with a old motherboard that I have no clue who it's made by, and a 80 gigabyte harddrive. The harddrive being about 2 years old compared to the computer's seven years. I still can't find out how much ram i've got.  

I'm still not sure what's causing it. I've got two ideas though. 
1) maybe I partitioned it wrong (quite a few times along with the Ubuntu installer) 
2) something's still on the Disk so it still wants to boot that. 
3) I have no clue what i'm doing and this is a common problem that you can solve by typing some cryptic command at the shell. :)

Any suggestions on how to make this boot?

---

### Post by nad on 2005-04-30
Try this command at the grub prompt: find /boot/grub/stage1 .

Now issue this command, all on one line, if the find command returns (hd0,0), otherwise replace the instances in the command with the correct digit(s):

install (hd0,0)/boot/grub/stage1 d (hd0) (hd0,0)/boot/grub/stage2 p (hd0,0)/boot/grub/menu.lst

Type: boot  and see what happens.

---

