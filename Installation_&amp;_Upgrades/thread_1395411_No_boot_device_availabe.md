---
title: "No boot device availabe"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by Fusilli Jerry on 2010-01-31
Hi folks,
 
This is my first post here and I'm a total Linux noob so please bear with me.
 
I've just installed Ubuntu on my XP desktop using the Wubi installer (I need to dual boot). I'm not quite sure of the version but I just downloaded it from the website today if that helps narrow it down. :)
 
The Wubi install seemed to proceed normally and when prompted to restart I did so. I choose Ubuntu at the screen where I am now prompted to choose between Windows XP and the Unbuntu OS. The installer then went through the process of completing the install and configuring the Ubuntu OS. So far so good.
 
This is where the problem starts:
 
During startup when I choose to load the Ubuntu OS I see a screen that displays GNU GRUB 1.97 beta 4. I'm not sure what to enter at the "sh:grub>" prompt so I typed "exit". At that point I see "No boot device available - strike F1 to retry boot, F2 for setup utility".
 
Here's some additional info that may be relevant. During the Wubi install I selected to install Ubuntu onto the "D" drive. The "C" and "D" drives are partitions of the same physical disk.
 
Please let me know what additional info you need and I'll do my best to provide it. Thanks for helping my conversion from the dark side. :)

---

### Post by meierfra. on 2010-01-31
You probably have been hit by a bug in Grub 2. See this link for more information and how to fix it:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

