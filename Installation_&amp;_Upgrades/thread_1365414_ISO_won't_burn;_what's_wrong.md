---
title: "ISO won't burn; what's wrong?"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by derekmbarnes on 2009-12-27
I understand this topic pops up all the time, so my apologies in advance for throwing on yet another one. But this is REALLY bugging me.

Here's the story: I'm going through the motions of acquiring the Ubuntu program on a Windows XP system...

-I downloaded and installed Infrarecorder.
-I downloaded Ubuntu-9.10-desktop-i386.iso. No problems.
-I downloaded and installed WinMD5.
-I checked the MD5 hash. All clear.
-I put a rewritable 700MB CD in my rewritable optical drive (insert tech support joke here). Again, no problems.
-I opened Infrarecorder, hit Burn Image, selected the Ubuntu ISO file, and hit OK.

BUT, no matter what configuration I try, I keep getting the same message: "Operation failed." I've done several simulated burns and one actual (unsuccessful) burn, and restarted my computer several times in the process to get the optical drive working again; I slowed the burn speed down to 1x (only to watch as it burned in 4x anyway); I tried SAO ("some files didn't like closing"), TAO (which didn't work at all) and raw-write method.

At this point I can only imagine the following possibilities:
1) It absolutely must be a "write once" CD-R and not a CD-RW
2) Infrarec isn't working properly
3) Windows XP is messing up the process, or
4) The computer just hates me.

If anyone has any insight, it is much appreciated. I'm more than ready to do away with Windows. (If you're going to recommend a different program than Infrarecorder, please explain why that program will do better.)

Many thanks,

Derek M. Barnes
Feeling n00bish

---

### Post by coffeecat on 2009-12-27
I've used InfraRecorder in both XP and Vista and I found it to be a reliable application - it was happy with rewritable discs too. So...

> **derekmbarnes said:**
> At this point I can only imagine the following possibilities:
1) It absolutely must be a "write once" CD-R and not a CD-RW
2) Infrarec isn't working properly
3) Windows XP is messing up the process, or
4) The computer just hates me.

... I wouldn't think so, but I can suggest a fifth possibility: perhaps the optical drive is failing.

I have another suggestion, but this will only work if your machine can boot up from a USB device. If it can, have a look here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Take note of the comment about 9.10 under 'Known issues'. All you need is a 1GB usb stick and you should be OK.

---

### Post by howefield on 2009-12-27
I also have used Infrarecorder previously without issue, but if you want to try another good free program, try CDBurnerXP.

If it still doesn't work, it would point to the disk or the burner as being the problem.

---

### Post by Bartender on 2009-12-27
I've read many times on the Ubuntu forums that you should use CD-R, not RW.

---

### Post by coffeecat on 2009-12-27
> **Bartender said:**
> I've read many times on the Ubuntu forums that you should use CD-R, not RW.

Never believe anything you read in a forum. :wink: I've been using CD-RWs for a couple of years now for installing Ubuntu and trying out other distros. No problems.

---

### Post by howefield on 2009-12-27
> **Bartender said:**
> I've read many times on the Ubuntu forums that you should use CD-R, not RW.

Credible examples ?

---

### Post by efflandt on 2009-12-27
I have never had any failures at all burning CD-R (or DVD+R) in any OS at 16x on my desktop or 12x on my laptop.  But my first experiences with CD-RW have been frustrating.

I first tried Brasero in Ubuntu which worked fine for CD-R, but failed my first attempts at CW-RW (blanking between attempts).  So I tried k3b and that worked the first time.  But then when I tried to do another, it ran endlessly for a couple of hours, probably trashing the disk.  And I could not cancel or kill k3b by any means (even kill -9), except by shutdown.

CD-RW apparently can be temperamental, has to burn at the proper speed (too fast does not clear data, or too slow can do a meltdown), but maybe my room temperature is too cool or my DVD/CD drive from 2004 is getting dusty.

But last time I bought CD-R they were 20 cents each, or if you want to go green you can to a live/install iso on bootable USB.  I even did bootable iso on 2 GB microSD (in SD adapter in USB card reader).  However, cheaper USB sticks can be slow (avoid SanDisk Cruzer w/U3), or may not last.

---

### Post by SecretCode on 2009-12-27
I would definitely suspect the drive is failing. It might fail less with a CD-R (as mentioned, CD-RWs are quite sensitive). 

Have you been able to burn anything else on this drive? Even an audio CD?

Also, what are the specs of the machine you are burning on? I regularly had burn failures on my last-laptop-but-one - the processor just couldn't handle it.

---

### Post by SecretCode on 2009-12-27
> **coffeecat said:**
> Never believe anything you read in a forum. :wink:
Including that ^

---

### Post by derekmbarnes on 2009-12-27
Thanks for all the help thus far. You guys work fast.

> **SecretCode said:**
> I would definitely suspect the drive is failing. It might fail less with a CD-R (as mentioned, CD-RWs are quite sensitive).

Have you been able to burn anything else on this drive? Even an audio CD?

Also, what are the specs of the machine you are burning on? I regularly had burn failures on my last-laptop-but-one - the processor just couldn't handle it.

It has been quite a while since I've used the burn drive. Considering how dusty the tray was when I opened it, I'm guessing the laser lens isn't doing any better...so yeah, it *just might* be the drive.

Then again, this computer was built when Pentium 4 was new. Fortunately I just got a new laptop for Christmas, which is what I'll eventually be installing on, and its burn drive will definitely be in better shape. I'll also try booting from USB as suggested, but from the looks of it that might end up being more complicated. (Plus I'd rather have the CDs to loan to other people in the future.)

I'll let you know how it works out...

---

### Post by raymondh on 2009-12-27
If you want to try a different burner ... reco a free [cdburnerXP]("http://cdburnerxp.se/").

Try it.  If it works, then you know infra was borked.  If it does not work, then it 'could' be the optical drive.

---

### Post by nerdtron on 2009-12-27
I also tried burning the .iso file in a CD-RW 700MB but they recommended CD-R 700MB in the ubuntu website (the .iso file is just 695MB right?).
I tried Nero burner, InfraRecorder, and even the default Windlose 7 image burner. But they all said "The data can't fit on the media (CD-RW)". 
Heck! Guess I need a CD-R but the nearby store ran out of CD-Rs so I went to [www.pendrivelinux.com](www.pendrivelinux.com) and followed the tutorials there to create a bootable flash drive with Karmic Koala. The steps are relatively easy to follow and booting from USB is not a problem on my PC. Installing Karmic on the hard drive is even faster using a flash drive.
Try it out!

---

### Post by derekmbarnes on 2009-12-28
Update: Tried the new burn drive and it worked just fine. No defects or anything. Not sure about the interface yet, so I'll be making another disk for Kubuntu to see if I like that any better.

Thanks, everyone! :D

---

