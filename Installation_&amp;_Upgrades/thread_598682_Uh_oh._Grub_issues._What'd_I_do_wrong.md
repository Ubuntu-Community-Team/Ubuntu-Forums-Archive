---
title: "Uh oh. Grub issues. What'd I do wrong?"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2007-10-31
Okay, somehow I screwed up several things and I swear up and down I have no idea how I possibly did.

So let's start with the drives. I have 3 drives in my computer. Drive A is Windows/Ubuntu split up 25gbWin 13gbUbuntuRoot and the remainder (203gbish) to my home dir. Drive B and C (sdb2 and hdd1) I use for rsync commands to back up my entire home directory to the other two drives. Well, I know I can install a new version of linux without formatting my home directory, however I wanted to play it safe so I ran both rsync commands which is NOTHING out of the ordinary.

Somehow I started getting errors I couldn't explain, something about lack of disk space. I was like what in the hell? I log out, go to log back in figuring it would "refresh" it... nope. Disk space maxed. Unable to load OS. I was like shiiiiiiit. Okay fine. So I put in the LiveCD and figured I'd explore drive A to delete some stuff... nope.

Okay, whatever. So I just get the 7.10 LiveCD (which I already had downloaded and burned to a CD) and figured I'd just redo the OS partition. Turns out I was using 13000 of 13004 of my Ubuntu Root that I somehow maxed. Seriously - I have no idea how I maxed it. My two rsync commands I use are as follows.

sudo rsync -a --progress --delete ~/ /media/sdb2
sudo rsync -a --progress --delete ~/ /media/IDEBackup

Okay, fine. So I do my thing and reinstall the OS. My main drive which had Windows and Linux installed was partitioned like so...

25gb - Windows
2gb - Swap
13gb - EXT3 (mounted as root)
203gb - EXT (mounted as home)

Where's the problem here? I even found a dual boot tutorial on UbuntuForums and they confirmed I did it right.

Yet when I boot 

- Linux - Error 22 Partition doesn't exist.
- Windows - Error 14 Something about unexecutable format.

WHAT CAN I DOOOO??

---

### Post by Roasted on 2007-10-31
Okay. Let me put it this way, since I'm hoping to wake up to an answer and get this system running.

I need to get grub running. We all know that.

How do I do a full reinstallation of grub? I have an Ubuntu 7.10 LiveCD as well as an Alternative CD from Edgy I believe.

---

### Post by Roasted on 2007-11-01
Okay, I said the hell with it and did a fresh install of windows and linux. Not a big deal since the only thing on windows is counterstrike. But nonetheless, I'm still curious to know what I can do in the future to avoid that. Every time I upgrade my version of Ubuntu, I get that error, yet I follow the suggested directions on here. Then I come here with problems and I never get an answer, so I always do a fresh install.

So, if anybody has anything, like a fix for what I can do next time this happens, please tell me!

---

