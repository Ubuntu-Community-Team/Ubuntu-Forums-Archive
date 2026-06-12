---
title: "Unique Dual Boot Problem"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by ramo on 2007-02-03
Here's my story:

This computer is 7 years old, but had the graphics card updated from a TNT2 to a 9600XT and added a second 250gig hard drive along with the 80gig that already came with the system plus I added an extra 256mb stick of ram to make a total of 512. It's running on an ancient Pentium 4 Willamette-core running @ 1.6GHz, doesn't even support DDR memory - only PC133 or less. Anyway, that's just a quick background on the computer itself, here's the installation issue at hand...

The computer's an HP Pavilion. Before shipping out with recovery CDs, HP decided the best solution would be to have a recovery partition on the hard disk - so this one time, my entire hard disk got wiped and I had to order the recovery disks (7 in total :mad:) Cost me $30 as oppose to paying $100+ for a pure version of XP. Alas, the recovery disks still create a hidden recovery partition at the beginning of the hard disk! How's this a problem? Well.. when I tried to install Ubuntu on the completely clean secondary 80 Gig hard drive (I switched the two hard disks around so that the 250gb is master and the 80gb slave) all worked well as far as Ubuntu went. So I rebooted and through the boot options that Ubuntu had installed, I chose to start "WindowsNT/2000/XP" and then it started the HP System Recovery from the recovery partition!! I think HP has some unique booting method incorporated in the recovery partition or something and it's f***ing up my dual-boot Ubuntu installation!! Any suggestions as to how to work around this problem? With these recovery disks I have, I have no other option but to install XP on the primary disk, so installing it on the slave hard disk is out of the question. And I'm not buying or pirating a fresh copy of XP nor am I going to ditch XP. 

Plus - can anybody direct me to an XP to Ubuntu/Linux introduction guide or something? The short period of time I had Ubuntu installed, I was trying to get my wireless router to work through ndiswrapper, but I had no idea how to install the goddamn files that I downloaded - they were all just a bunch of text files!! And where can I find the command prompt? 

I have the desktop version of Ubuntu Linux 10.6 btw the way, thanks ahead of time ):P

edit: Ok, I've included an attached screenie that shows the situation of the partitions. On an added note, the 80Gb hard drives has about 7.5mb at the end of the hard disk that is unallocated and can't be allocated. Any ideas on that?

---

### Post by confused57 on 2007-02-03
> **ramo said:**
> Here's my story:

This computer is 7 years old, but had the graphics card updated from a TNT2 to a 9600XT and added a second 250gig hard drive along with the 80gig that already came with the system plus I added an extra 256mb stick of ram to make a total of 512. It's running on an ancient Pentium 4 Willamette-core running @ 1.6GHz, doesn't even support DDR memory - only PC133 or less. Anyway, that's just a quick background on the computer itself, here's the installation issue at hand...

The computer's an HP Pavilion. Before shipping out with recovery CDs, HP decided the best solution would be to have a recovery partition on the hard disk - so this one time, my entire hard disk got wiped and I had to order the recovery disks (7 in total :mad:) Cost me $30 as oppose to paying $100+ for a pure version of XP. Alas, the recovery disks still create a hidden recovery partition at the beginning of the hard disk! How's this a problem? Well.. when I tried to install Ubuntu on the completely clean secondary 80 Gig hard drive (I switched the two hard disks around so that the 250gb is master and the 80gb slave) all worked well as far as Ubuntu went. So I rebooted and through the boot options that Ubuntu had installed, I chose to start "WindowsNT/2000/XP" and then it started the HP System Recovery from the recovery partition!! I think HP has some unique booting method incorporated in the recovery partition or something and it's f***ing up my dual-boot Ubuntu installation!! Any suggestions as to how to work around this problem? With these recovery disks I have, I have no other option but to install XP on the primary disk, so installing it on the slave hard disk is out of the question. And I'm not buying or pirating a fresh copy of XP nor am I going to ditch XP. 

Plus - can anybody direct me to an XP to Ubuntu/Linux introduction guide or something? The short period of time I had Ubuntu installed, I was trying to get my wireless router to work through ndiswrapper, but I had no idea how to install the goddamn files that I downloaded - they were all just a bunch of text files!! And where can I find the command prompt? 

I have the desktop version of Ubuntu Linux 10.6 btw the way, thanks ahead of time ):P

edit: Ok, I've included an attached screenie that shows the situation of the partitions. On an added note, the 80Gb hard drives has about 7.5mb at the end of the hard disk that is unallocated and can't be allocated. Any ideas on that?

What you could try is: at the grub menu at startup, scroll down to highlight your Windows entry in grub, press "e"(for edit), then change the line with root (hd0,0) to root (hd0,1) & see if Windows will boot.  This change is only temporary, to make it permanent, you'd need to change it in your /boot/grub/menu.lst file.

You can download the "Official Ubuntu Book":
[http://www.ubuntuforums.org/showthread.php?t=339531&highlight=ubuntu+book](http://www.ubuntuforums.org/showthread.php?t=339531&highlight=ubuntu+book)

---

### Post by ramo on 2007-02-03
I'm really sorry, I'm a total nublet at Linux - what the hell is grub?

edit: Let me clarify what my install does - I boot from the cd, and when Ubuntu is opened up, I press the hard drive icon with the arrow on it that install it to the hard drive and it takes me through this windowed install thing, is that grub?

---

### Post by confused57 on 2007-02-03
> **ramo said:**
> I'm really sorry, I'm a total nublet at Linux - what the hell is grub?
What I'm referring to is the grub menu at startup that shows the boot options(Windows & Ubuntu)...you'd press the arrow down key to highlight your Windows entry, then press the letter "e" key, this will allow you to highlight the line with root (hd0,0)...then you can change it to root (hd0,1), there's a menu at the bottom of the screen that will guide you as to what keys to press to boot, go back to main menu, etc.  If Windows will boot with this change, then we can go about making it permanent.

The grub menu shows up just after your bios does it's POST thing, if it doesn't automatically show up, then there should be a prompt to press "Esc" to display the boot menu...if I'm understanding you correctly.

Add:  Your Windows recovery partition is probably on the first partition root (hd0,0) and your Windows installation is on root (hd0,1)...what's happening is that you're booting into root (hd0,0), which is your recovery partition.  In grub, (hd0,0) is the first partition on your first hard drive, same as hda1 in linux(which has a different numbering system).

---

### Post by ramo on 2007-02-03
Oh, so Grub is the boot manager, basically. Now what's changing this h0,0 stuff gonna do exactly, can you explain plz? 

sorry if I'm being buggy :lolflag:

---

### Post by ramo on 2007-02-03
I don't want to have to re-install windows now because it takes a long time with the 7 cd recovery system, can anybody be sure about this? I attached a screenie of my partition/hard drive layout and I explained my problem in the first post. What can I do, considering the current configuration, to have the computer boot up normally? 

A separate question, can I just have Ubuntu boot 100% straight from a hard drive? Does it have to be through Grub? Because Grub and that HP Recovery partition are giving me trouble right now... hey wait, I can choose where to put Grub in the initial install right? Can I put it on the secondary slave hard drive? and how can I do that? I don't mind having to change the boot location in BIOS, that's fine by me, I'd prefer that actually

---

