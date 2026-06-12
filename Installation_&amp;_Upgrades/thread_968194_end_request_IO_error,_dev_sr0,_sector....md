---
title: "end_request: I/O error, dev sr0, sector..."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by LilyAyanami on 2008-11-02
I just upgraded to 8.10 using the Synaptic Package Manager.  I'm getting the following error when I boot with a disk in the CD/DVD drive. 

> end_request: I/O error, dev sr0, sector 216176
Buffer I/O error on device sr0, logical block 54044


 The following is an excerpt from kern.log:
> 
Nov  2 07:15:00 Melchior kernel: [   27.942989] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov  2 07:15:00 Melchior kernel: [   27.942991] sr 4:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Nov  2 07:15:00 Melchior kernel: [   27.942994] end_request: I/O error, dev sr0, sector 216176
Nov  2 07:15:00 Melchior kernel: [   27.942995] Buffer I/O error on device sr0, logical block 54044
Nov  2 07:15:00 Melchior kernel: [   33.288241] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

The error message repeats, but Ubuntu does eventually load.  The error message stops when I eject the CD.  I do not get the error message at all when I boot with an empty CD/DVD drive.  However, the drive works after Ubuntu is loaded.  I can read CDs and DVDs just fine.

I did not see this error in 8.04.

a) Is anyone else having this issue?
b) How can I resolve this issue?

System:
MB: ASUS M3A32-MVP Deluxe
CPU: AMD Phenom 9850 Quad-Core
Memory: 4GB
CD/DVD: Sony CD-RW/DVD-+RW DRU-840A

Thank you very much!

---

### Post by bluesxman on 2008-11-03
I'm seeing this too, following upgrade to 8.10. Same symptoms, remove the CD, system boots fine.

---

### Post by lisati on 2008-11-03
I had a similar message when getting ready for a fresh install on my laptop. The installation seems to have worked, and I haven't seen it since.

---

### Post by panfist on 2008-11-06
I had the same errors, installation complete now, and everything seems OK but I am still worried.

edit:
I forgot to mention, installing via a SATA optical drive didn't work. It would hang indefinitely after I selected the language and pressed enter to install. I had to plug in an old IDE drive, and it worked, after the IO errors.

---

### Post by bartruji on 2008-11-11
Same error with 8.10 as well.

---

### Post by TAGJM on 2008-11-11
Me too.. and my USB Wireless Network Adapter is not working now too.  Switched to XP to check out the forums. Being a complete Newb to Linux OS - I dont know where to look to fix the USB Network Adapter problem.  Any suggestions?

---

### Post by zeisel on 2009-02-05
I am having the same problem.  Is there a problem with the new ISO image (I downloaded it)? The error I'm getting is:

126.083412: end_request: I/O error, dev sr0 sector 1431176
126.08467: Buffer I/O error on device sr0, logical block 178897

I've also burned through 5 cd's with the same errors each time.  

I've also changed out both my SATA HD with and IDE and CD/DVD drive for another.

Does someone with a bigger brain that I have know what might be the challenge?

---

### Post by SteelGuy21 on 2009-02-06
I'm having the same i/o error.  System locks up after I get the error.  This is a new install with a SATA HD. Thought it could be BIOS setting but I've been through there several times.  Could this just be an issue with a new installation onto a SATA drive?

---

### Post by whatteaux on 2009-02-07
This might be similar to what has been reported as a bug for several months now:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/304954](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/304954)

...but with no sign of a fix or resolution yet.

---

### Post by alexdrudi on 2009-02-15
[SIZE="5"]**SOLVED**[/SIZE]

[http://ubuntuforums.org/showthread.php?t=1015569](http://ubuntuforums.org/showthread.php?t=1015569)

always add "solved" in your Google search query ;)

---

### Post by bswanboat on 2009-10-17
SOLVED!

Thansk for the details, for it got me to think outside of the box. In this case it was the wrong cable to the CD-ROM. The speed is now much faster!

---

### Post by sseng_123 on 2009-12-09
:popcorn:Im new to Ubuntu and I have the same issue. I have a brand new Toshiba Satellite Laptop L500-1EN. To my knowledge, the hard drive is SATA and not IDE.
Im still struggling to rectify the issue.
 
The Ubuntu version im trying to install is Ubuntu 9.10.
So anyone who has some advice should assist me

---

### Post by jaya28inside on 2010-06-12
> **sseng_123 said:**
> :popcorn:Im new to Ubuntu and I have the same issue. I have a brand new Toshiba Satellite Laptop L500-1EN. To my knowledge, the hard drive is SATA and not IDE.
Im still struggling to rectify the issue.
 
The Ubuntu version im trying to install is Ubuntu 9.10.
So anyone who has some advice should assist me

what's your error message anyway? :p

---

### Post by Krazzy on 2010-10-01
Hello, I had the same problem and I Disabled "AHCI" mode in Bios and everything ran and worked fine.
 
Hope this helps someone,
Krazzy.

---

### Post by SheaMan on 2011-11-15
I got fifty or so of these at the end of installation, but when I rebooted without the cd everything came up fine :shrug:

---

### Post by oldos2er on 2011-11-16
Closed, necromancy.

---

