---
title: "Unable to find a medium containing a live file system"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by TSellers on 2011-04-27
I have tried burning a number of ISO's of 101.10 and 11.04 to DVD and intalling them on 2 of my desktop machines. I eventually see: ('initramfs) Unable to find a medium containing a live file system'

The thought just occurred to me as I type this, perhaps I can only install from a CD and not a DVD?

---

### Post by xd20 on 2011-04-27
I got this error as well.  What I did was removed my graphics card and turned on onboard graphics, and Ubuntu installs fine.  Then you go and get the proprietary drivers for your graphics card and turn off the onboard graphics.

Unfortunately for me, once I turned on my graphics card again, ubuntu failed to work, and would only work with onboard graphics.  Dunno why this issue occurs, and neither does anyone else in the entire community, otherwise I would have resolved it by now.

So good luck.

---

### Post by TSellers on 2011-04-27
Thanks for that. Ironically I went to put a different graphics card in it the other day, but the board was too old to accept it, so I had to leave the old Matrox card in it. I think I'm going to face up to the need to upgrade the whole system. And just when I thought I would never buy another ATI card ever again, I see the threads in here today explaining how nVidia with Optimus can not work with Linux. Oh well, guess that still leaves the Intel graphics.

---

### Post by Rubi1200 on 2011-04-27
You should check the integrity of the image and CD:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by TSellers on 2011-04-27
Thanks, I'll give that a try, all I did so far was run the file check from the boot screen as suggested in the forum, but just got that reuslt as reported above.

---

### Post by Rubi1200 on 2011-04-27
Also, consider burning another CD at the slowest possible speed. It's not foolproof, but I have seen that error before where either the hash didn't match or the CD was defective or had not been burned slowly enough.

edit: you are not using them to try and install Wubi right? Because that won't work from a DVD install, only CD.

---

### Post by TSellers on 2011-04-27
THanks, I must have read you mind, because I just stared to burn a CD-R a few minutes ago. I'm burning with UltraISO and although I had the 3X speed option picked, when I launched it it went straight to 10X, but I guess I'll see what happens. If that does not work then maybe I will try Deepburner at a slower speed.

---

### Post by djupsilon on 2011-04-28
I get the exact same error, except the CD with 10.10 works perfectly. I checked the MD5 sum and it checked out and I also tried burning at lower speeds but same error. I'm really disappointed with this release. The image I tried out was the 64 bit desktop version.

Motherboard: Asus P5B Deluxe (set to AHCI)
DVD: Pioneer DVR-216D SATA

---

### Post by TSellers on 2011-04-28
That's interesting (I've been trying the 32bit). I had those results with 10.10 on a DVD. I think I'll burn 10.10 to a CD and see if I have any better luck then. THanks for the head's up, I'll keep my fingers crossed.

---

### Post by djupsilon on 2011-04-28
Let us know how it works out for you. I tried both 32bit and 64bit 10.10 CD before and they work fine on 4 computers that I've tried.

EDIT: I tried out the 32bit image for 11.04 from a different mirror and it still won't work on my desktop (same error) but it does work on my old laptop.

---

### Post by TSellers on 2011-04-28
Thanks,

I just burned 10.10 to a CD-R instead of a DVD at the slowest speed Deepburner would allow (10X) but still no joy on the desktop I'm trying, just get a bunch of different lines of ASCII text that is still scrolling on the screen after 30 minutes or so.

I previously was trying 11.04 Beta, and now I see there is a desktop release, so maybe I will also try that.

It seems that it does not like the older hardware that I'm using, an Intel P 2.6 MOBO and Matrox AGP Video card. Probably I should hunt around for a different video card for starters and see it that helps, but I thought I had Ubuntu working on the Matrox a year or so ago and it was a widely supported card in its day.

---

### Post by TSellers on 2011-04-28
In desperation I unpacked the 11.04 ISO to a USB device and ran the Wubi.exe. I got an error that it could not find the required installation files after about 5 minutes.

I see the procedure to install Ubuntu TO a USB device, I can't seem to find the proper method to install FROm a USB device using the device as the file store, when I tried it before it insists on going to the internet to download the files all over again, and then results in the same error as noted above. Am I going about the method to install from a USB device wrong?

---

### Post by djupsilon on 2011-04-28
Well I had 10.10 running on an old AMD 1 GHZ with a Geforce 2 AGP and it worked fine and in fact with the Nvidia drivers I was even able to turn on the fancy desktop effects and that's probably older than your system.

As for making the USB stick, there's some instructions here [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
If you go to step 2 and choose USB stick and click show me how, it gives step by step on how to create it.

---

### Post by TSellers on 2011-04-28
This system is determined to try my patience, and I think it has won the fight. Now I regret not checking out those newer looking boxes sitting in the Electronics Recycling tent at the town dump the other day. 

I was able to make the USB bootable, and then in the BIOS enable 'Boot from USB'. However try as I might, I still could not see the USB as a bootable device option when you choose your boot device sequence, so the system just goes ahead and boots into Windows as normal. In Windows, if I run Wubi I get the error mentioned above. Sounds like it's time to write this project off, at least for this particular machine, thanks for all the help!

---

### Post by Shepherd X on 2011-04-29
I'm getting the same "unable to find a medium containing a live file system"

I didn't have this problem when I installed Ubuntu 10.10 nor any of its derivatives. I usually have to use "nomodeset" so that the screen doesn't go out of range, but here it isn't working. I'm wondering if there is a bug in the install procedure for some setups? I checked the integrity of the image by checking the md5sum, but there isn't a problem there. Any suggestions?

---

### Post by djupsilon on 2011-04-29
are you running off a CD or a USB stick?

---

### Post by Shepherd X on 2011-04-29
I'm running it off a CD. I did an integrity check of the CD, it's fine. I tried making another copy and checking the integrity of both the iso file and the burnt cd. They were fine, but I get the same error when I try to install using the CD. My BIOS don't allow booting off a USB stick. My desktop has an an old Nvidia video card (ge force fx 5200) with 128 mb ram, 1 gb system memory, 2.8 ghz celeron cpu. Any suggestions?

---

### Post by djupsilon on 2011-04-29
Do you already have Windows or Ubuntu installed? From Windows you can run wubi off the CD to install Ubuntu. From Ubuntu you can directly upgrade it. Also there's a method to create a boot floppy in order to install off a USB stick.

I also did an MD5 check of every file on the CD and it's good so clearly there's something wrong with the installer in 11.04.

---

### Post by Shepherd X on 2011-04-29
No, I don't have Windows installed. The only operating system I have installed now is Linux Mint 10. I wanted to go back to Ubuntu with Natty because I like the whole idea of a new and innovative shell, regardless of how much people criticize it.

---

### Post by djupsilon on 2011-04-29
Ah, in that case I think your only solution is to try to make a bootable floppy and then install off a USB stick. I found a link on that here [https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

Hope it helps. If it doesn't work then just wait for Mint 11 which will have gnome 3.

---

### Post by Shepherd X on 2011-04-29
I don't have a floppy drive on this machine. The only bootable media on my pc is the dvd drive. I can boot off the Ubuntu natty disc fine, it just never finishes and instead takes me to that annoying message "unable to find a medium containing a live file system." I hope this can be resolved quickly.

I'm going to try the alternate install cd (non-graphical). If it works, then the problem must be something with the video card not being properly supported. But that would be strange, since it worked fine with the 10.10 install.

---

### Post by djupsilon on 2011-04-29
From what I've read it's an issue with the DVD drive not being detected which is kind of weird considering we are able to start the installer off the DVD in the first place. Let us know if the alternate install cd works for you.

---

### Post by Shepherd X on 2011-04-30
I was able to successfully install using the alternate install cd. I guess anyone who is having the same problem should also use that CD.

---

### Post by djupsilon on 2011-04-30
Glad to hear it worked for you. I'm looking to make the live CD for 11.04 work as it did in 10.10. I submitted a bug on launchpad.

---

### Post by Bloodspike on 2011-11-01
> **TSellers said:**
> I have tried burning a number of ISO's of 101.10 and 11.04 to DVD and intalling them on 2 of my desktop machines. I eventually see: ('initramfs) Unable to find a medium containing a live file system'

The thought just occurred to me as I type this, perhaps I can only install from a CD and not a DVD?


I just had a similar problem, I tried to boot Ubuntu 11.10 Desktop 32 and 64 bit and got the same "('initramfs) Unable to find a medium containing a live file system" error.  I ran MD5 on both my ISO images but both are fine.  I finally used an external USB DVD drive to install with.  Just wanted to add to that for anyone having this issue.

---

