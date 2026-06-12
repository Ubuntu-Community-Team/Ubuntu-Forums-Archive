---
title: "Can't install Dapper"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by jsiii on 2006-08-21
Hello, I have serious troubles installing Dapper Drake. Here is my story.

* I had Breezy 64bit installed.
* I received message through update manager that new release is available.
* I accepted an offer and started upgrade.
* I was asked if I want to replace few user scripts that have been changed.
* I refused as I wanted to keep my settings.
* After this process, X wouldn't run.
* I decided to reinstall Ubuntu anew.
* As I did have some troubles with 64bit version I decided to go on with 386 version.
* I downloaded Dapper ISO and burned CD.
* It was nearly impossible to run the installation as the process froze at random locations. Many times even during Live loading.
* On tenth try or so, I finally managed to install Dapper using CD rom.
* I run that and started update process. It froze and from that point I was not able to run Dapper again.
* I installed Breezy 32bit and run upgrade to Dapper through update manager.
* It went fine but every time I run Dapper, it starts loading desktop and freezes during that process. Once it even froze on login screen. I also get some messages: "Input not supported" from my digital monitor that take too much I think.
* During Linux loading, there is this error: "Starting PCMCIA services: Failed"

Note: I did not have any problems with Breezy at all 

Any advice?
Thank you.

---

### Post by wpshooter on 2006-08-21
Are you trying to install from the DESKTOP CD or from the ALTERNATE CD ?

Also, how are you downloading and burning the Ubuntu ISO ?

Are you checking the integrity of the Ubuntu ISO cd by using the sum check utility that is located on the initial boot screen ?

---

### Post by jsiii on 2006-08-21
I used Desktop CD

I downloaded file from official webpages and burned it with two different burning programs

Integrity check passed with zero errors. Also when I use MD5 file to check it from Windows it is alright.

PS: Now I noticed that on the web there is new version of ISO 6.06.01, I will try it. Before I used 6.06.

---

### Post by randell6564 on 2006-08-21
Hi!

Please post a little about your PC. 

It's strange!  I started the same way you did.  I burned and installed Breezy (fell in love with ubuntu), then I got the same update message from update manager that you did.  I went for it and had no problems!  

I'm thinking that it's got to be hardware issues!  The same goes for downloading and burning iso's.  I have downloaded so many iso's from so many disto's that I stopped keeping track and have never had a corrupted burn!

---

### Post by jsiii on 2006-08-22
AMD64 1800+, 512 RAM, ATI Radeon 9200 (not sure about this one, I am at work now ;-)

I am nearly sure it has something to do with graphics in live mode.

* I downloaded new version of Ubuntu ISO 6.06.01 and it broke down again during loading of live.
* I run that in safe graphics mode and everything went smoothly.
* I installed graphic drivers and so on and so far after one update and two restarts everything works fine.

---

### Post by randell6564 on 2006-08-22
> **jsiii said:**
> AMD64 1800+, 512 RAM, ATI Radeon 9200 (not sure about this one, I am at work now ;-)

I am nearly sure it has something to do with graphics in live mode.

* I downloaded new version of Ubuntu ISO 6.06.01 and it broke down again during loading of live.
* I run that in safe graphics mode and everything went smoothly.
* I installed graphic drivers and so on and so far after one update and two restarts everything works fine.

I'm glad you got it figured out, but I'm using a ATI Radeon 9200 and it works fine. weird!

---

### Post by jsiii on 2006-08-23
Hmm, It was premature optimism. After I returned from work the other day and tried to fire up Ubuntu, I ended up with black blank screen.

When starting Linux "Starting PCMCIA services" does not have "failed" attached. However "ok" is not there as well (just nothing is there :-) Other services seem to be ok.

Needless to say I did not have any problems neither with XPs nor Breezy.

---

### Post by Mé®LíN on 2006-08-23
This may be of interest:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

Bet you wish you hadn't reinstalled.. :P

---

### Post by jsiii on 2006-08-24
Thanks, I will give it a try...

---

### Post by jsiii on 2006-08-25
I suppose that it was the problem. I tried the solution from the suggested thread and X server was not working anymore. So I installed the whole Ubuntu anew and it is working now.

Thanks for help everyone.

---

### Post by jsiii on 2006-09-07
Ok, it's been a while since my last post.

Since then I was practicing reinstalling Ubuntu on a daily basis as it just stopped working at random times and during random operations. Most of the times I ended up with blank screen and dead monitor during boot. Usually it happened when I turned off the PC in the evening going to sleep (after session of restarting and configuring mouse under X without problems)... it did not worked the other day.

I used various CD sources for installation (including Ubuntu official CDs)... There was a problem during installation as it always froze at random times and I had to run it in Safe Graphics mode. In safe graphics mode, it was ok.

My PC is pretty new (8 months) and it ran few OS's without any problems (Win XP, React OS, Ubuntu 5.10)...

I am hugely disappointed. Something is rotten in Dapper Drake.

My configuration:
AMD Sempron 3000+ (the processor is 64bit but I am running x86 Ubuntu as 64bit is missing features), 512MB RAM, ATI RADEON 9600

---

### Post by tvgm2 on 2006-09-09
I have the same exact symptoms as you:
Random lockups/restarts when trying to install 6.06.1
Random lockups/restarts aftering installing with alternative
Random lockups/restarts while booting or updating the OS
Breezy works but I can't get to the Internet with that

My setup:
Biostar 6100 AM2
AMD 4200 X2
Leadtek 6600GT PCI-X
2 SATA HDDs

I'm using the CDs that were shipped to me as well as downloaded Breezy and alternative.  They all pass the md5 check.

---

### Post by jsiii on 2006-09-13
I am nearly sure it has something to do with ATI drivers. Like I said, on the boot I ended up with turned off monitor. I booted using recovery mode, reinstalled ATI drivers and reconfigured X following this tutorial

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

After that Ubuntu was working again. But not the other day. Now I am only waiting for Edgy to resolve this problem. And if it does not help my next thread will be "How to get rid of Ubuntu and Grub" :-(

---

### Post by jsiii on 2006-11-02
Ok, same problems with Edgy. I already invested so much time trying to install Ubuntu that doing badly paid hard labor I would already earned enough to buy ten copies of Vista Ultimate Edition. Pretty disappointed with this :-( I am just repeating that my PC is in quite good shape, and it had no problem running Breezy and WinXPs.

---

### Post by jsiii on 2007-04-23
So, very similar problems with Feisty. Plus few new problems. I was thinking about trying Kubuntu. Do you think it may resolve some problems, I mean is Kubuntu different enough to give me a different set of bugs? :-)

I don't want to give up the Linux. Ubuntu just does not seem to be usable. I would also like to learn Linux deeper. So Debian might be option too.

**UPDATE** - Yesterday, I installed openSUSE and so far, I am quite happy with it. I already had some problems and was able to fix them. I am not saying I dislike Ubuntu, but openSUSE did much better job. Anyway. Ubuntu, thank you for bringing me to linux :-)

---

