---
title: "Live CD works but doesn't install"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by arte54 on 2010-11-14
Well, I'm a ( non native speaker ) Ubuntu newby.
 
If I run Ubuntu 10.4 LIVE from CD everything works fine.
However, when I try to install, it hangs up at about 23% ( while installing Firefox ).
 
I thought my HD had a problem, but the same happened after checking it had no bad sectors and even after replacing it.
 
Same as above using a CD of version 8.4 ( live works, install doesn't complete).
 
Same trying the Alternate in place of the Desktop edition.
 
With the same CD's I already installed successfully on other machines.
 
Booting from USB SHOULD be possible ( according to BIOS settings ) but apparently it doesn't work.
 
Present machine characteristics :
 
AMD Athlon 2200+ 1.8 Ghz
512 MB RAM
HD EIDE 40 GB ( Master of the Primary channel )
BIOS AMI dated 13-05-2003
Motherboard : no brand
Two EIDE CD drives ( as Master and Slave of the Secondary channel )
 
What should I try next ?
<Give up> is not an option !

---

### Post by coffee412 on 2010-11-14
> **arte54 said:**
> Well, I'm a ( non native speaker ) Ubuntu newby.
 
If I run Ubuntu 10.4 LIVE from CD everything works fine.
However, when I try to install, it hangs up at about 23% ( while installing Firefox ).
 
I thought my HD had a problem, but the same happened after checking it had no bad sectors and even after replacing it.
 
Same as above using a CD of version 8.4 ( live works, install doesn't complete).
 
Same trying the Alternate in place of the Desktop edition.
 
With the same CD's I already installed successfully on other machines.
 
Booting from USB SHOULD be possible ( according to BIOS settings ) but apparently it doesn't work.
 
Present machine characteristics :
 
AMD Athlon 2200+ 1.8 Ghz
512 MB RAM
HD EIDE 40 GB ( Master of the Primary channel )
BIOS AMI dated 13-05-2003
Motherboard : no brand
Two EIDE CD drives ( as Master and Slave of the Secondary channel )
 
What should I try next ?
<Give up> is not an option !

If you have an onboard video card it might be using system memory to run. I once got around this by going into bios and telling system to use 64 megs of system ram instead of the 128 or 256. Otherwise you just might need a bit more memory.

Perhaps borrow from another system for the install or just pick some up somewhere.

---

### Post by arte54 on 2010-11-14
Thank you coffee412 !
I'll try the way you suggested.

---

### Post by sikander3786 on 2010-11-14
Hi.

You've checked your HDD for bad sectors but it'd be worthy to try replacing your HDD's data cable, CD/DVD drive data cable or even the CD/DVD drive itself.

Also make sure your system or CD/DVD drive is not heating up during the process.

You said that you've tested the same disc with other systems and installation is successful there so I'd not force you to check the disc or the image for defects :-)

> Booting from USB SHOULD be possible ( according to BIOS settings ) but apparently it doesn't work.

What happens when you try to boot from USB? Does Bios even recognize your USB drive?

How did you prepare your USB? See here for instructions.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

And it might also be related to RAM as mentioned above.

Ubuntu will definitely work with 512 MB RAM but I doubt it will not perform that well.

For 512 MB RAM, I'd recommend Lubuntu. A light weight fork of Ubuntu.

[http://lubuntu.org](http://lubuntu.org)

---

