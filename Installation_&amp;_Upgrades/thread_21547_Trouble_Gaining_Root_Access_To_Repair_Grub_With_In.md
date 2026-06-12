---
title: "Trouble Gaining Root Access To Repair Grub With Install Disc"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by smedstadc on 2005-03-22
Hello, after consulting the existing information and many many grub re-install threads, and also the sections of ubuntuguide.org I still can't figure out my problem, so I've come to the forums for help.

**Problem:** 
My problem is one of my roomates in college saw me using Ubuntu one day and asked me to help him switch to Linux. He wanted to be able to do his schoolwork on a stable computer that wouldn't be incredibly vulnerable to malware and viruses on the school network. (We occasionally have problems with this) So, he made the switch to 4.10 and liked it. One day he decided that he'd like to play one of his games, and decided to install windows on some unpartitioned space, he didn't realize that this would cause GRUB to stop working. (I never had the opportunity to warn him)

**Steps I have already taken:** 
First I followed the instructions for gaining root access with an install cd, [here](http://www.ubuntuguide.org/#gainrootinstallcd)

I determined that ```
/dev/discs/disc0/disc/part1
```  was the ubuntu partition, and following the next instruction I attempted to mount the partition on at the ```
/ubuntu
``` directory I had created with the following command (as per instruction):
 ```
mount /dev/discs/disc0/disc/part /ubuntu/
``` 
This is where I am forced to stop because I get an error saying that the mount failed because of an invalid argument, and occasionally the error would be that I'm trying to mount something that isn't mentioned in the ```
fstab
``` file.

I can't follow the instructions to reconfigure grub unless I can mount the drive and chroot it, at least this is what I've learned from all the information I've found. I'd appreciate it if someone could help me with this, because you wouldn't be helping just me, but you'd be helping the multiple people on this forum who are having a similar problem and haven't been given a good answer yet. (I've noticed multiple unanswered posts on the same topic as mine. I'm hoping the detail I've provided helps a little.

---

### Post by bored2k on 2005-03-22
My advice is this: forget about warty disc.
Download and burn [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) .

Boot with it , and with the included MBRtool, wipe grub/xp boot loader from your mbr . This will make nothing bootable. After this, reinstall Windows first , then Install Ubuntu .

I mess up a lot of systems, and whiping mbr's most of the times do the trick for me .

Word of advice: **backup** .

And welcome to the forums buddie . Check out Jdodson linux games list .

---

### Post by smedstadc on 2005-03-22
I think thats a terrible idea. My entire goal was to preserve the existing ubuntu installation and make both systems bootable through grub.

Though, thanks for the help anyways. I actually figured out what the problem was with mounting the drive. I ran e2fsck on it with the install console held down the 'y' key for about a minute and it mounted just fine after fixing an incredible amount of errors.

Now on to reconfiguring the menu.lst

---

### Post by bored2k on 2005-03-22
[QUOTE=smedstadc]I think thats a terrible idea. My entire goal was to preserve the existing ubuntu installation and make both systems bootable through grub.

Though, thanks for the help anyways. I actually figured out what the problem was with mounting the drive. I ran e2fsck on it with the install console held down the 'y' key for about a minute and it mounted just fine after fixing an incredible amount of errors.

Now on to reconfiguring the menu.lst[/QUOTE]
 Uh ... sir , you do know you can wipe your mbr AND install grub from scratch right , w/o having to reinstall ?

Anyway, ignore me and bonne chance.

---

