---
title: "Upgrade Windows Hard Drive"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by Bosonator on 2006-09-17
Greetings,

I have a dual-boot Kubuntu 6.06 / Windows XP Home system, with each OS installed on a separate IDE hard drive. I would like to replace my Windows drive with a larger one, without disrupting my Kubuntu install, naturally 8-) . 

Here's my game plan - I'd like for someone to take a look at this and tell me if you see any holes in it!

Definitions
----------- 
Kub. drive = current Kubuntu drive
Win. drive = current (10 GB) Windows install
New. drive = new (20 GB) drive, destined for Win XP install

Note
----
The Kub. drive is in the slave position, and the Win. drive is in the master position.

Plan
----
1. Remove both Kub and Win drives
2. Install New drive in master position
3. Install WinXP to the New drive
4. Replace the Kub drive into the slave position
5. Do something with GRUB?
6. Ready to go?

Step 5 seems to be the weakest part of my plan at this point, so help here would be appreciated ;).

***Bonus Points!***
If you can direct me to information about how to just copy my existing WinXP install to the new drive (without needing a fresh install --- I only use WinXP for games and home recording, so it hasn't really gotten buggered up enough to necessitate that).

---

### Post by catlett on 2006-09-17
You can use your listed method and use this process to restore grub [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Or you can clone your drive with this freeware application [http://www.miray.de/products/sat.hdclone.html](http://www.miray.de/products/sat.hdclone.html)
Also check your hard drive cd. Some of the manufacturers include an app for transferring data to the new drive.

---

### Post by Bosonator on 2006-09-17
Thanks for the info. I may need some help first with installing the drives. If I just unplug my Kub. drive and plug in the new drive (in the slave position, so I can copy over my files), GRUB comes up when I boot and says "error 17", then does nothing. Suggestions? Thx!

---

### Post by catlett on 2006-09-17
You will have to make a grub floppy. You have parts of grub on both your hard drives. If you remove either one, grub won't work. With grub on the floppy, you do not need anythimng on the drive, Anyways, make it with these instructions [http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

---

