---
title: "can't install ubuntu"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2012-01-30
My machine is an old Dell Precision 420 mt. In the past I had Fedora 6 running perfectly, so I put a new disk and attempted to install 11.10 from a CD. Checked for errors in the CD and everything was fine. However after a few minutes with the splash (Ubuntu / .....) the system freezes and can only get out with a hard reset. I tried with the alternate install and the same thing happened. So I tried other installations such as Centos and Fedora and the same thing happened. So I decided to install XP for later using Wubi. The XP installation went fine without a hitch and when I ran wubi.exe I got the message saying:

There is no disk in the drive. Please insert a disk into drive \Device\Harddisk2\DR1

with a pop-up window giving 3 options "cancel", "continue" and "wait". I pushed several times these buttons and finally started downloading the tar.gz file to install, and later while it was expanding it just quit.

Apparently my machine does not communicate with the linux installer about the HD that is present. In the BIOS I disabled any device that was not being used such as the ZIP drive, the floppies and the second CD rom, but the problem remains.

I will appreciate any help.

Daniel

---

### Post by carl4926 on 2012-01-30
What are the machine specs?
Does F6 still install?

---

### Post by sikander3786 on 2012-01-30
You probably need to enable 'acpi=off' or 'nomodeset' at the Boot Options page. As soon as the computer starts booting from the Ubuntu medium, keep pressing any key and you'll see the Boot Options page. Press F6 there and try with different parameters. All this is explained here:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Also take a look here:

[http://www.tuxgarage.com/2011/02/common-installation-problems-with.html](http://www.tuxgarage.com/2011/02/common-installation-problems-with.html)

---

### Post by danielsender on 2012-01-30
I don't longer have the Fedora6 CD, so I couldn't try. In fact I tried with those options after hitting F6 as well as other combinations. I also tried the all_generic_ide=1 and still refuses to install. Today I'll try physically unplugging the ZIP drive which was disabled from the BIOS. I'll keep you posted. Thanks for the replies.

Daniel

---

### Post by danielsender on 2012-02-04
I physically disconnected the zip drive and still hangs while showing the 5 dots on the splash screen. I tried with the suggested different boot options and the problem remains.
What is puzzling to me is that windows XP installs without any problem, I wonder what is the difference in the installation that makes any linux distribution fail.

Daniel

---

### Post by danielsender on 2012-02-04
I ran a few experiments. I pushed the ESC key as soon as the purple screen came on. The first line shown is:

/init: line 7: can't open /dev/sdb: no medium found

and a bunch of lines saying things like:

skipping nonexistent file ...

etc.

So just to make sure that there wasn't any issue with the CD drive(s) I made a bootable pen drive with UnetBootin and when I clicked on "try without installing" it starts and writes the same line as when I use the CD. This CD as well as the pen drive starts perfectly fine in other machines.

---

### Post by danielsender on 2012-02-06
I'm about the quit. I played with some settings in the BIOS such as the IRQ, etc. but I have no clue of what is the problem. I also tried ALL possible alternate boot options, one by one, but the installation keeps freezing at different points. What a disappointment!!!

---

### Post by carl4926 on 2012-02-06
bios settings:
 IDE as Compatible
 SATA as AHCI ?

---

### Post by bepperk on 2012-02-07
i have the same problem.

---

### Post by guwaposai on 2012-02-07
i'm having the same issue... the installation seems to freezing up on this message:

"skipping hardreset on occupied port..." <<< what does this usually mean guru's :(

---

### Post by Mosome on 2012-02-07
You might want to check your DMA settings for your hard drive in your BIOS.  Maybe try configuring any other settings to a different notch.  Sometimes it can take some experimentation if this is the case.

Another thing to consider is that you said you have an old machine.  The message said skip, but with the other error messages then maybe that wasn't the right BIOS settings.  I'm sure the interrupts should be left where they are when it was working.

When its performing a fdisk, or formatting the disk, it has to lock it down so the file system that it's newly creating isn't messed up.  If it's that old, like < 2 Ghz then it will take some time to partition a disk... (about 30-60 minutes)

---

### Post by mastablasta on 2012-02-07
> **danielsender said:**
> What is puzzling to me is that windows XP installs without any problem, I wonder what is the difference in the installation that makes any linux distribution fail.
 
 
xp is from 2001, Linux that you tried is i think from at least 2007 or so. different kernels... maybe some support for certain device you are using got dropped.
 
> /init: line 7: can't open /dev/sdb: no medium found

 
this means it was looking for your other hard drive (you have two drives in BIOS right?) that you have defined and it could not find it or it could not open if for some reason.

---

### Post by mastablasta on 2012-02-07
> **guwaposai said:**
> i'm having the same issue... got this screenshot... i hope this is explain what i'm going through :(
 
 
your issue is not the same. 
 
try to install directly from boot or using alternate cd.

---

### Post by guwaposai on 2012-02-07
i already tried installing through boot... same issue with the screenshot... i can't seem to progress with the installation... i'll try a different CD then...

thanks guys and more power :popcorn:!

---

### Post by danielsender on 2012-02-11
Today I swapped the memory sticks and it didn't make any difference. The process freezes way before formatting the disk. As I understand it,  the live CD can be used even if there is no HD, right?
This is not the oldest machine on which I installed Linux. What is frustrating to me is that no message comes up, it OK's every line through the different steps, and suddenly no mas...

---

