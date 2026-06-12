---
title: "Problems installing Xubuntu 12-04.1 on old computer."
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by david senior on 2012-12-05
I have an 1999 vintage computer - a top of the range (at it's time) desktop with an AMD Athlon processor running at ~1GHz. The graphics card is an nVIDIA G-FORCE FX 5200 put in in, I think, about 2005. I have recently upgraded the memory from 250MB to 1.5GB using very cheap SDRAM PC113 memory cards. I have been running Ubuntu 8.10 with no problems, both before and after the memory upgrade. (Running the 'mem test' program after the upgrade results in a 'no errors' report - it takes about 2 hours). I have used this computer to create both alternate and desktop installation CDs (i386) for Xubuntu 12.4.1. On attempting to boot the computer from the desktop CD, the CD is read for about a minute then everything stops with a blue screen. (The same thing happens if I try to boot live versions of various newer distros from DVDs provided with magazines). I can boot the alternate CD and have used the 'check disk integrity' facility on this to verify it is OK. If I attempt to use it install to another hard disk on the same computer, this goes through OK and on booting from this hard disk I can see both the new installation and the old Ubuntu 8.10 in the grub display. The old version still works the same but the new Xubuntu 12.4.1 fails to start. I can start it using 'recovery mode' and it comes up with a 'root@ubuntu' prompt. If I use the same alternate CD to install Xubuntu 12.4.1 onto a USB stick I find I can boot this - and it works perfectly - on a newer netbook computer. It is as if my old computer has problems with newer distros but, as far as I can find out, any AMD Athlon processor should be i386 compatible. The hard drives are IDE not SATA. Any suggestions welcome.

---

### Post by trogdor1138 on 2012-12-06
Your computer is definitely at least i386-compatible, as even 64-bit processors can execute 32-bit code. That at least answers your image version question.

I'd be willing to bet that your computer is actually booting just fine, but either a kernel module or default driver isn't playing nice with your Nvidia card. Do you have speakers connected, and when the screen goes blue or blanks do you ever hear the Ubuntu startup theme? This would be an easy way to determine if it's actually booting or not.

Also, does that card have multiple outputs? Sometimes it's as simple as switching to a different port, or checking all ports for output.

Finally, I would suggest reading up on the "nouveau" driver since that's what Ubuntu will try to use by default for your GPU.

---

### Post by mastablasta on 2012-12-06
you could also try minimal iso. i think it uses different (non PAE) kernel: 
 
Mini iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
install guide: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
instead of icewm mentioned in the guide install xubuntu-desktop.
 
can the image boot on the old computer as well?

---

### Post by david senior on 2012-12-06
Thanks to both. I tried the minimal iso (with md5sum OK) but the installation crashed immediately after answering the 'HTTP proxy' question (which I left blank). The thought occurred to me that I had done the original alternate disk installation without the computer online, despite the installation procedure asking for this, so I repeated the installation with the computer online. This also asked the 'HTTP proxy' question which I again left blank (I wouldn't have known how to answer it otherwise) and this time it went through. When trying to boot the installation it still failed to boot directly but if I went via the recovery mode I got the panel which included the option to to continue the normal boot and this *then worked OK* - I had a working desktop!

The installation works well with basic browsing and Gimp, for example, (possibly benefiting from my memory upgrade) but it will not work with Adobe Flash or any sound application. (Installing the available upgrades does not change this).

All this contrasts with the behaviour of my newer netbook on which the installation was done without the computer online and which has none of these problems. If I boot this into the recovery mode it behaves exactly like the desktop now does with the option to continue a normal boot (but, of course I do not have to do this).

I can see there could well be problems of compatibility of later Linux cores with older hardware if updates to the core had inadvertently led to these - presumably it would be impossible to test new cores with all older hardware. I also wonder if hardware compatibility would also be an issue with Adobe Flash. Perhaps the only way of fully recovering the computer would be to buy new graphics and sound cards but I also worry that I am having problems with the installation process - perhaps because of the older hard drive specs.


UPDATE ADDED LATER

Just to round this off - some further observations:

1.  All that above about the effect of  being online or not when installing  was a red herring - retrying offline gave the same result as online - I  don't know what went wrong the first time ;

2.  When up and  running I looked at the 'other drivers' available and this offered a  driver for my nVIDIA card but installing this resulted in the boot not  working again (either direct or via recovery mode) - I had to  re-install;

3.  I tried the original 1999 graphics card that came  with the computer (I originally changed this since I didn't have the  Windows driver) and this **booted both via the recovery mode and  directly** (albeit going though some rather flakey screens on the way  and still no luck with Adobe Flash).

Conclusion - It seems almost  certain that, as suggested by the above contributors, I am dealing with  graphics card compatibility issues but, at least,  I have some sort of a  get-around to make it worth not binning the computer just yet! I may or  may not look into these issues further but thanks again to the above.

---

