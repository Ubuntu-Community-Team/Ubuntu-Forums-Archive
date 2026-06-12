---
title: "Better Safe Than Sorry: questions before installing ubuntu"
date: 2004-11-27
forum: Installation &amp; Upgrades
---

### Post by clueless on 2004-11-27
Hello to all,

I am a new member of the forum, new to linux (although I do know stuff about computers and windows) and new (hopefully) to ubuntu. It's been more than a year that I'm trying to migrate to linux and as time goes by I am always more determined. 

I am currently downloading ubuntu and intend on installing it and hopefully getting rid of windows. I have tried other distributions but have never been really happy with the results. Main reason of my failures is insufficient knowledge, although I'm still reading whatever I find online, forums, documentation etc. But each and every one of these failures has managed (in the hard way) to give me some more knowledge.

So my questions are:
1) I first intend to make a dual - boot system because I really have many Gigs and precious to me information that I don't want to lose, and it's really difficult to make image CDs of 2x80GB hard drives. But once I tried to install Fedora Core 2 and even though it didn't touch my windows partitions, it made me lose all information in them (I found something about LBA and stuff I didn't exactly understand mentioned afterwards in various forums). Is there any such danger here? If so what should I do to be sure I don't lose any of the information stored? I have already made linux partitions, that are just sitting there waiting to be used.

2) The only real reason I can't completely migrate to linux is that I only have a web access through my cell phone (GPRS). It's a motorola C336, USB connection. I have been searching a lot but never did find information on how to use it as a GPRS modem. Mandrake couldn't even recognize the device and there don't to seem to be any drivers around for it either. I also have another phone I could use if needed, a Nokia 6510 with infrared connection, but I think that cable is always  better/easier.

I have seen posts on a forum asking "why are people so interested in linux when obviously windows can do everything and much painlessly?". I agree about the painlessly part, I wouldn't know which OS is better, but my answer is that it makes you part of a great community and that only is worth the extra effort.

---

### Post by Rancoras on 2004-11-27
Welcome to the community!

In response to question 1:  You could possibly have the LBA problem with Ubuntu as well.  If you don't want to risk losing data, there's no substitute for a good backup.  It's always advisable to backup your stuff before doing something this drastic to your computer.  If problems arise when trying to reboot to windows, check your BIOS settings first and make sure the primary HDD is set to LBA and not AUTO.  During install you will get to a point where GRUB will be installed, make sure the installation detects your windows installation.  If it does, you should have no problems.

Question 2:  I have no idea what, if any, GPRS phones are supported by linux.  Remember, Google is your friend.

*Moving this to the more appropriate forum - Installation

---

### Post by clueless on 2004-11-30
Thank you very much for your help, Rankoras,

I have downloaded the .iso and did try to install it, after backing up my system in a hard drive. But the installer just locks when I'm choosing the partitions on which to install. After the first mouse click it just freezes and even if I can move the mouse pointer, I can't click on anything nor does my keyboard work. I had the same problem on trying to install Mandrake 10.1 community and official but I have never been able to figure that out.

I decided though that maybe I shouldn't play around with my system too much, so I'm assembling back an old pc, a Pentium 2 @ 266Mhz with 64 MB RAM and a 12GB hard drive. I'll have it ready in a couple of days and that's where I'm gonna experiment, till I feel confident enough to install on my main computer.

So I'm just posting to say thanks for the help and if I find out what the reason is for the installation freezing at this point I'll post it, who knows if it could help anyone else.

---

### Post by adbak on 2004-11-30
For using Google to search for Linux help, it's always helpful to check out [http://www.google.com/linux](http://www.google.com/linux) .

And if I remember correctly, there should be no mouse for the installer part.

Perhaps next time you try to install, right after you pop the CD in and you first see the Ubuntu screen, try typing "linux custom".  That will give you the most basic (basic in the literal sense of the word) packages needed.  See if you get this far.  If you can, you may just have to reinstall normally over the custom installation.

Worth a shot.

---

### Post by clueless on 2004-12-01
Yes, right the installer is text only, I was confused because I have the same problem installing Mandrake. On Ubuntu the computer freezes, so keyboard doesn't respond, on Mandrake too, with the only thing that responds is the mouse pointer but not being able to click.

I have been trying for weeks now to find out what the problem is (on Mandrake) but I haven't found anything. I will try installing your way too. But if it doesn't work either I think it's much safer and easier installing it on the other computer and use it just to learn.

---

