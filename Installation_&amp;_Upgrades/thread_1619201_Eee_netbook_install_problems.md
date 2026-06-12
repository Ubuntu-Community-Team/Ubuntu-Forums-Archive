---
title: "Eee netbook install problems"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by M0d1 on 2010-11-11
I have searched the forums and even tried an advanced search but I have not found a solution to this problem.
 
I was running a Eee pc with Windows 7 starter but after a faulty hard drive, my fiance had something to do with that :P, I decided to switch over to Ubuntu 10.10 netbook (I have replaced the hard drive and everything seems to be working normally). I am able to boot from a usb drive and run Ubuntu from the USB drive.  The problem that I am facing is that when I install Ubuntu it tries to read my cd-rom for more files and then gives me an apt configuration error.
 
I have downloaded the kernel twice and have tried with both unetbootin and universal usb creator so i do not think that it is a bad download error.  I have tried persistent and non persistent usb drives and have even tried to add a snippet of code to the install that reads "cdrom-detect/try-usb=true".  Nothing seems to work and I just am hoping for a little help from the Ubuntu community :). 
 
I am more than willing to answer any questions to the best of my ability.
 
Thank you

---

### Post by M0d1 on 2010-11-14
Well, I hate to bump my post but I was wondering if anyone has any ideas. I can buy and external cd-drive and install from an iso but I was hoping to find a way to install from my usb.  Any help would be appreciated.

---

### Post by Jechem on 2010-11-14
what EEE do you have?  you can get help from here also. [http://forum.eeeuser.com/](http://forum.eeeuser.com/) help here are more EEE specific. 
check this also if this is related to your problem [http://ubuntuforums.org/showthread.php?t=1615558](http://ubuntuforums.org/showthread.php?t=1615558)

---

### Post by M0d1 on 2010-11-14
Thank you for input :).
 
I have a EEE pc 1005Hab. 
 
**Processor** Intel Atom N270 / 1.6 GHz.
**Hard Drive** 160.0 GB - Serial ATA-150 - 5400.0 rpm.
 
That ubuntu forums thread did not really help. I have started to read through the EEEpc forums and I will post in here if I find a solution.  I do not think it is a hardware issue.  I think that it keeps trying to get files from a cd rom drive that is nonexistant.  I think that it is just a simple coding problem but I do not know exactly what to change or where to go to change it.  I have never messed with kernels before with my programming.

---

### Post by Jechem on 2010-11-14
bthomson ( [http://forum.eeeuser.com/viewtopic.php?id=89835](http://forum.eeeuser.com/viewtopic.php?id=89835) ) has installed 10.10 on his 1005hab but he has problems with his internal mic. Have you tried 10.04? maybe 10.10 has some incompatibility issues with your hard drive.

---

### Post by M0d1 on 2010-11-18
I decided against trying to install it from a USB drive and instead bought an external dvd drive and installed it that way.  It proves that it wasn't my hard drive just a code issue in the kernel.

I would still like to figure out a solution to the problem just in case I ever want to install from a USB.

---

### Post by Hawkoon on 2010-11-18
> **M0d1 said:**
> I would still like to figure out a solution to the problem just in case I ever want to install from a USB.

I installed 10.04 on my Eee901 from a USB live stick, no problems except for flaky wifi+wpa2 connenction. I used the Netbook ISO version to make the USB stick. I never tried it with the standard desktop or the alternate ISO versions. Did you try out all the ISO versions?

EDIT: I can only boot my live stick when made NON-persistent. Never figured out why.

---

### Post by movieman on 2010-11-18
> **Jechem said:**
> bthomson ( [http://forum.eeeuser.com/viewtopic.php?id=89835](http://forum.eeeuser.com/viewtopic.php?id=89835) ) has installed 10.10 on his 1005hab but he has problems with his internal mic

10.10 seems to work perfectly on my 1005HAB, though I haven't tried the microphone. I installed from an external DVD-ROM drive too.

---

### Post by Jechem on 2010-11-18
> **movieman said:**
> 10.10 seems to work perfectly on my 1005HAB, though I haven't tried the microphone. I installed from an external DVD-ROM drive too.

looks like its a hit and miss for 10.10. I tried it also on my 701 4G everything worked but it slowed down after a while. maybe coz my cpu can't keep up so I went back to 10.04.

---

### Post by galvatron408 on 2010-11-18
I installed via kickstart and it worked well too. I have an eee pc 1000.

---

### Post by M0d1 on 2010-11-19
> **Hawkoon said:**
> I used the Netbook ISO version to make the USB stick. I never tried it with the standard desktop or the alternate ISO versions.

I actually did try with the standard desktop version and had the same problem.  The funny thing is that I used the same ISO that I installed for the the USB on the cd but since I actually had an external cd drive connected it was able to grab the files instead of giving me an error and crashing.

Side note: aptitude is freaking awesome. I had a friend that is studying to be software engineer look at my netbook to help me install java and php for some classes i am working on.  He showed me aptitude in the terminal and it makes life a lot easier.

---

