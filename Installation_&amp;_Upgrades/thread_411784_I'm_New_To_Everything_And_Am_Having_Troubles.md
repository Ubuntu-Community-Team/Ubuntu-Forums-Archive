---
title: "I'm New To Everything And Am Having Troubles"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by Ph0biA on 2007-04-17
Ok. Let me start out with this. I've never used linux, macs, anything that's not windows, ect. I know my way around windows, not enough to code, but to personalize so to speak. Well, a bit ago I got a new computer. It's AMD x64 ect. Well, I installed windows xp and got a crack for it, it said genuine and worked for a while until I restarted and said I needed to activate, I clicked ok, it then said I was already activated, didnt make any sense, but I clicked ok, it logged me out and I clicked login, it again said I hadnt activated, so I clicked OK again and it then asked me to activate, I used a link on the thing to get to IE which I then used to go to my C:/ drive and get on my MSN messenger, my friend sent me here, said I didnt even have to uninstall windows (which is good because I can still use it if I just get around a few things). So I downloaded you're disk and ran it and what not; put my CD drive as boot up first drive, ran the disc and click Start or Install Ubuntu. After a while, I was working on Linux (Ubuntu or w/e) for the first time. Well, I decided to turn off the comp for the night; when I booted up in the morning, It started up as windows XP. I guess my first question would be; what should I do? I want Ubuntu to be my default OS, and I also want to keep XP because I have data on there that I want to keep. So what should I do? (also bear in mind, I put the disc back in and played it and all it let me do was install it again... so I started Ubuntu with nothing....)

---

### Post by jakev383 on 2007-04-17
> **Ph0biA said:**
> Ok. Let me start out with this. I've never used linux, macs, anything that's not windows, ect. I know my way around windows, not enough to code, but to personalize so to speak. Well, a bit ago I got a new computer. It's AMD x64 ect. Well, I installed windows xp and got a crack for it, it said genuine and worked for a while until I restarted and said I needed to activate, I clicked ok, it then said I was already activated, didnt make any sense, but I clicked ok, it logged me out and I clicked login, it again said I hadnt activated, so I clicked OK again and it then asked me to activate, I used a link on the thing to get to IE which I then used to go to my C:/ drive and get on my MSN messenger, my friend sent me here, said I didnt even have to uninstall windows (which is good because I can still use it if I just get around a few things). So I downloaded you're disk and ran it and what not; put my CD drive as boot up first drive, ran the disc and click Start or Install Ubuntu. After a while, I was working on Linux (Ubuntu or w/e) for the first time. Well, I decided to turn off the comp for the night; when I booted up in the morning, It started up as windows XP. I guess my first question would be; what should I do? I want Ubuntu to be my default OS, and I also want to keep XP because I have data on there that I want to keep. So what should I do? (also bear in mind, I put the disc back in and played it and all it let me do was install it again... so I started Ubuntu with nothing....)

You'll want to dual-boot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
My advice? Buy a real copy of Windows. Linux is getting easier, but it's not for everyone yet. You will need to know some things about computers and not be afraid to get in and modify the guts of the OS, especially if you want your 64bit stuff to work.
Good luck!

---

### Post by Ph0biA on 2007-04-17
Well I've been using computers since I was 5 years old. Im 18 now; and I've done registry hacks on my own windows computer, ect. Not to brag, but I know more than anyone in my class about registy hacks and using computers in general. Practically. I've had instructors from other buildings call me in class to come fix their computers, once again, I'm not bragging, just verifying my own intellect about computers. I'm ready to do this.

Back to your post, when I installed ubuntu, thats what I did, but instead of coming up with those screens, it asked me to start or install. I hit enter, and thats the only window that came up, it started ubuntu without anything else, no questions or anything, just started, that causes a problem because now that I restart, I can choose the ubuntu OS, it automatically chooses windows... it doesnt come up with a choice or anything.

---

### Post by badactress on 2007-04-17
Are you sure you've actually installed Ubuntu? From what you say I suspect you may have just run it from the live CD. This allows you to play around with Ubuntu without actually installing it on your hard drive. If this is the case, then do exactly as you did before, but once you have Ubuntu running, there should be an icon on your desktop called "Install" or something similar. Clicking this will begin the process of installing Ubuntu to your hard drive. It will let you set up a dual-boot system where you can choose when you switch your computer on, whether to boot into Windows or Ubuntu. 

If you want to keep Windows I'd advise defragging your drive (in Windows) before installing Ubuntu.

The install process is fairly simple if you let the installer do it all for you automatically, but it's still worth reading a few forum posts on the subject.

and as always.. back up any important data you have on the computer as things can and do go wrong!

Good luck! Any problems just ask here & somebody will be quick to help..

---

### Post by darrenm on 2007-04-17
I assume you didnt click the install icon on the desktop after the CD has booted. The CD gets you into a live version of the operating system, considerably slower than a full hard disk install.

---

### Post by Ph0biA on 2007-04-17
> **darrenm said:**
> I assume you didnt click the install icon on the desktop after the CD has booted. The CD gets you into a live version of the operating system, considerably slower than a full hard disk install.

That was it! Once again, I was thwarted by the power of reading....

Do I need to do something with partions? I've been told something about that.

---

### Post by rillip on 2007-04-17
The installer has a manager called gparted, which will let you resize your partitions without destroying them and creates a partition out of the free space.  This is part of why you should defrag first.

And not to dismiss your abilities, but no ammount of Windows skill really makes you prepared for Linux.  Most of Linux work is done from the command prompt; almost none of Windows is.  IMO, the only way to get ready for Linux is to use Linux (or Unix or BSD, but let's not open that can of worms), so I think Ubuntu is a good place to start, but don't have the expectation that it will all be point and click, or that everything will go smoothly from the start.  Usually it does, but sometimes you'll run into issues that take a lot of searching and trial and error.

---

### Post by Ph0biA on 2007-04-17
Alright, well, how much of a 250 GB hard drive should I partion?

---

### Post by darrenm on 2007-04-17
> **Ph0biA said:**
> Alright, well, how much of a 250 GB hard drive should I partion?
Think of how much you will be using Windows over Ubuntu or vice versa and partition accordingly.

If you have lots of videos and music already in Windows then dont make Ubuntu too big, you can access them from in Ubuntu anyway.

---

### Post by jakev383 on 2007-04-17
> **Ph0biA said:**
> Alright, well, how much of a 250 GB hard drive should I partion?

On my dualboot desktop I use 20G for Windows, 20G for Ubuntu, and the rest as a FAT32 share (120G for me) so I can share the files easily between the two.

---

### Post by darrenm on 2007-04-17
Given the choice between the two, for a shared partition I would probably use Ext3 instead of FAT because you have a very stable Windows ext3 driver, you can use Linux permissions on it and you get journalling on it inside Linux. Oh and it won't fragment ;)

---

### Post by jakev383 on 2007-04-17
> **darrenm said:**
> Given the choice between the two, for a shared partition I would probably use Ext3 instead of FAT because you have a very stable Windows ext3 driver, you can use Linux permissions on it and you get journalling on it inside Linux. Oh and it won't fragment ;)
Did the ext3 thing finally become stable? I had used one a long time ago, but it broke with SP2 and never worked after that....

---

### Post by darrenm on 2007-04-17
Yeah it just runs ext3 as ext2 (ie doesnt support journalling) and everythings mounted as root due to the obvious Windows limitations. I had one glitch once that was not reproduceable so I pretended it didn't happen and put it down to Windows :)

Although NTFS-3G is now at version 1.0 and considered production stable so theres no reason not to use NTFS between the 2 or just do away with a shared partition altogether.

---

### Post by rillip on 2007-04-18
I tried an ntfs share and never got it to mount.  I'd suggest Fat32 on the first try, because it's one of the few I've seen that "just works" like most everything else.  You can always switch it up later, and frankly to the casual user it won't make two farts worth of difference for a shared partition what the file system is so long as it works.

---

### Post by Ph0biA on 2007-04-18
> **rillip said:**
> I tried an ntfs share and never got it to mount.  I'd suggest Fat32 on the first try, because it's one of the few I've seen that "just works" like most everything else.  You can always switch it up later, and frankly to the casual user it won't make two farts worth of difference for a shared partition what the file system is so long as it works.

Well, I finally got it set up; is there anything that I need to download (apart from updates)? Does avi files work on linux? Sorry; I'm new to linux (I was able to customize it to look mostly like OS X, but thats about it {I used tutorial}).

I also cant listen to the music on my myspace, why is that? (I downloaded the adobe flash player but it wouldn't install).

---

### Post by darrenm on 2007-04-18
Are you running Feisty?

---

### Post by Ph0biA on 2007-04-18
> **darrenm said:**
> Are you running Feisty?

Nope, 6.10 Edgy

---

### Post by rillip on 2007-04-18
Yes, it can handle avi files quite nicely.  You'll need to install the restricted codes.  There's a section in the FAQ on the board that has this, and is probably a sticky over in the media forum.  As for not playing the sound in myspace, I'm not familiar with what technology they're using. You say you download flash but it wouldn't install; I'm betting you didn't get the Linux version.  Search arround on the net about linux flash upgrade, I'm sure you'll find a tutorial like I did for Firefox.  Once I followed that I had no problems with YouTube, for example, but the quality is a little meh at best.  Flash for Linux is a little out of date and weak, but I don't have much need for it on a day to day basis,

---

### Post by Ph0biA on 2007-04-18
> **rillip said:**
> Yes, it can handle avi files quite nicely.  You'll need to install the restricted codes.  There's a section in the FAQ on the board that has this, and is probably a sticky over in the media forum.  As for not playing the sound in myspace, I'm not familiar with what technology they're using. You say you download flash but it wouldn't install; I'm betting you didn't get the Linux version.  Search arround on the net about linux flash upgrade, I'm sure you'll find a tutorial like I did for Firefox.  Once I followed that I had no problems with YouTube, for example, but the quality is a little meh at best.  Flash for Linux is a little out of date and weak, but I don't have much need for it on a day to day basis,

Thats the thing, I downloaded the linux version. It also said something about java, should I install that too?

---

### Post by jakev383 on 2007-04-19
Go download Automatix and install the stuff there (codecs, Java, etc.)
[www.getautomatix.com](www.getautomatix.com)
That will make it easier to install all the stuff you're looking for.

---

