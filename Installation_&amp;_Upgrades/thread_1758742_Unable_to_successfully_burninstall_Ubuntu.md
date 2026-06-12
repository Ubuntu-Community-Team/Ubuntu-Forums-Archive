---
title: "Unable to successfully burn/install Ubuntu"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by tangerinefight on 2011-05-15
HI everybody. Let me preface this by saying that I am probably going to sound like an idiot to most of you, and this is long, but please bear with me. I had been a lifelong Windows user until January of this year, when my HP laptop quit functioning well enough for me to use it even for the most basic things. At this point I was lucky enough for my parents to offer to buy me a Mac, which another story entirely, but I've been using that since.

I used Ubuntu for a very brief period of time when I dual-booted Ubuntu and Windows on said HP laptop. At the time I had a friend who uses only Linux OS' for all of his computers so he was very familiar with the system, but for some reason we couldn't configure Ubuntu to connect to the internet so I stopped using it. That's all the experience I've had with it basically.

Anyway, recently I wanted to restore my HP to it's factory settings and sell it to my friend who is going to be entering college and needs a computer to do her homework on. I was not sent a system restore disk with my HP laptop and realized only after I proceeded with the restoring process (/deleting my Windows OS and all files) that I did not have a new OS to install on it. That was a moment of genius on my part, I know. 

I decided it would be a good idea to burn a disk with Ubuntu on it and put that on my HP laptop because I don't have to pay for it and it will probably run better than it ever did with Windows Vista, so I can finally just get it to my friend. Here is where I'm having issues. I attempted to burn the image to a CD-R as per the instructions on this site; [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I followed all of these instructions to a T. Yet, when I checked to make sure the CD burned correctly (also as per the images on that page), I see only the one file in the folder, not the files that should be there. I am able to view all of the files that SHOULD be on the CD in finder, and I even tried dragging all of them into the disk utility, which doesn't work. The .iso file is the only oen that will move, and apparently that didn't do what I needed it to.

That page isn't helpful in my situation because it only tells me what to do starting from a blank slate. I'm wondering how I can get the rest of the files I need onto the CD. 

Also, since the PC I am hoping to install this on doesn't currently have an operating system (even though it seems like Windows was re-installed somewhat? When I start the computer it will show me the Windows Vista logo/background, makes the welcome noise, and shows user accounts but when I try to use the computer it says "your account has been disabled" or "Windows could not complete the installation. To install windows on this computer restart the installation"). 

^ This information I only added because I'm wondering, does anyone know if I will be able to install a different OS on this computer now? Is it too far gone? I guess I could always sell it for parts but I feel like this is a matter of me just needing to figure out what the hell I'm doing wrong. 

Thanks to anyone who read that wall of text and if you can help me out I will be forever grateful. I'm no longer friends with the Ubuntu-enthusiast I mentioned before so I can't ask him for help. Hopefully someone here will know.

---

### Post by Quackers on 2011-05-15
Welcome to UF :-)
It may well be the case that your HP laptop has a recovery partition which will recover the system to the state it was in the day you bought it. (Unless that partition has been deleted!)
There will be a key that you need to press during boot to activate that partition and run the recovery. Have a mooch around and see if you can find the correct key.
With regard to the Ubuntu cd, have you tried booting from the cd? Obviously the cd drive would need to be the first bootable device in your bios - may need changing.

---

### Post by wilee-nilee on 2011-05-15
What OS are you using to burn the cd, if it's MS W7 is a right click burn to cd If XP get imgburn and use it, Vista probably has a right click if not get imgburn as well.
[http://www.imgburn.com/](http://www.imgburn.com/)

If Ubuntu use brasero or install gnomebaker, always burn as an image.

Check the MD5SUM sum of the ISO and the cd as well if needed.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you get this burned and booted; before installing open gparted and as Quackers suggested look for a recovery partition on the HD.

---

### Post by pablopancho on 2011-05-15
Hi, as I understand you burned the iso file onto the cd (by dragging the iso file on the cd?). If that is the case then this was wrong approach. The proper way is to burn the iso image using 'Burn an image' or 'Burn from image' option in your burning software. I recommend ImgBurn for Windows. The thing is that on the cd there should be files that are inside the iso image, not the iso file itself. 

Of course damaged Windows on your hard disk doesn't prevent you from installing Ubuntu. 

It is not clear to me if you have a second computer that you can use to burn Ubuntu iso image. If you have then try burning it once again, this time not by dragging the iso file but by using the right option. If you don't have then you need to ask someone to burn it for you.

---

