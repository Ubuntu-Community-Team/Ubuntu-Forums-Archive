---
title: "Slowest installation EVER ubuntu 16.04.3 LTS"
date: 2018-01-02
forum: Installation &amp; Upgrades
---

### Post by dav123456789 on 2018-01-02
Hi,

I'm not often on the forums as a simple user of ubuntu... the last one i installed was 10LTS... years ago... But i know a "bit" about computers. (industrial C/C++ dev for years + got my own computer shop a couple of years).

And here i am, because i can't find a solution, in fact i don't even understand the problem as the install is now completely silent...

I am trying to install ubuntu 16.04.3 LTS on a new computer i'm building for a friend :


Processor : AMD A6 9500E
Motherboard : Gigabyte GA-A320MA-M.2 (chipset AMD A320)
RAM : HyperX Predator 8Gb
HDD : Kingston SSD UV400 120Gb

I did mount the iso on a bootable USB device with RUFUS.
Bios is UEFI, SATA is AHCI.

And there i am !


I can launch the installation (i have the good old menu that ask me if i want to go live CD or install). Hit install...
And there it goes EXTREMELY slow. After 15 minutes i get the language to be chose, i click on french, and have to wait 4,30minutes to see it selected, then i hit next, 10 more minutes, now i'm at the next screen and there it goes, i need nearly 5 minutes to have the click taken in account, and 10 to go to next menu... i don't think this will do.
Mouse cursor move correctly outside this, Ethernet cable is connected but undetected.
Any help would be appreciated.
Thanks,
Dav

---

### Post by TheFu on 2018-01-02
Sounds like network timeouts either due to an unsupported NIC or DNS issues. Start there.  

Might be best to completely disconnect the networking for the installation, then come back and add whatever networking is needed.  Hopefully, the NIC is supported.  If there are any issues with a NIC, I put in a $25 Intel PRO/1000 card. Doing that will save all sorts of headaches for the life of the system.

Would be useful for you to learn and know the chip used in the networking on the machine ASAP.  lshw will show it.  So will lspci.

BTW, how does the live CD run?  That is always the first step to determine if the hardware is easily supported or not.

---

### Post by mörgæs on 2018-01-02
If hardware support has something to say, which is a likely explanation, then installing 18.04 (development version) would be worth the while for comparison.

I can't promise that 18.04 is stable enough for general use but still it's an interesting data point.

---

### Post by dav123456789 on 2018-01-02
@Thefu
This really doesn't look like networks timeout, it's not freeze/unfreeze, it's just incredibly slow, even the windows take several minutes between the first line appearing, to the moment it's active.
By the way, in fact i had network, it's just that it needed 30 minutes to show me the "connected" status, and 30 more minutes to show me the "disconnected" status when i unplugged the RJ45...
By the way i tried both with the RJ45 plugged and without it, nothing change in the speed.
The live CD have the same comportment, boot well and once on the desktop, nothing react in less than 15 minutes, except the mouse cursor which is moving smoothly.

@mörgaes thanks, i'll give it a try, i wished i could get a LTS for my friend, but if i have no choice... at least i'll see if there is a difference. edit : curses ! the 18.04 isn't released yet... Alpha 1 will be available the next week u_u'

I wonder, is there a way to include extra drivers in the installation pack ?

---

### Post by DuckHook on 2018-01-03
Have you tested both download and DVD burn for errors? Try running/installing from a LiveUSB instead. Have you tried installing with nomodeset? Also, try a memory test. The problem may be HW, especially in a brand new custom built system. As ex-computer shop guy, you already know the drill, but just as a doublecheck: Is RAM compatible with MOBO? Are BIOS settings proper (ie. do they match RAM physical speed)? Are you over/underclocking? Is MOBO expecting ECC RAM when you have non-ECC installed? Are RAM modules properly seated? Are all cards properly seated? Look for MOBO cracks. Etc.

From LiveDVD/CD, once on desktop, do <Ctrl>+<Alt>+<F1>, then:```
top
```…and:```
dmesg
```…for anything that looks out of ordinary.

If all of above fails: a long shot that may only serve as an additional data point, but you can also try downloading/installing FreeBSD to see if the problem isn't in the Linux kernel.

---

### Post by TheFu on 2018-01-03
This is all guess-work and experience driven advice at this point. ;(  Usually, Ubuntu installs require 15 minutes.  When I've had it take longer (45+min), it was a NIC issue. That's all.

Network support is just the first place to look, but that Gigabyte motherboard is a v1.0 release. Fairly new with USB3.1 and mSATA. Over the decades I've been supporting Linux, I've learned to avoid hardware that is extremely new.  Find it best to wait at least a year and to always check the internet for Linux support issues.  

Found this: [https://www.linuxquestions.org/questions/linux-hardware-18/is-gigabyte-ga-a320ma-m-2-motherboard-linux-compatible-4175614602/](https://www.linuxquestions.org/questions/linux-hardware-18/is-gigabyte-ga-a320ma-m-2-motherboard-linux-compatible-4175614602/) . A roundup of other people trying to get Linux working on that MB.  1 says that "Mint and Ubuntu don't work."

Sadly, it is still Windows-first on the bleeding edge, usually.  This appears to be the *bleeding* part with what I've seen about that MB.  Someone else here asked about it in September and there were zero replies. On paper, it looks like a nice MB.  I would return it and get something else if you still have time for the return. Call it an Xmas gift.

I've been looking to build a new Zyzen 1600 system for about 6 months. Happy that I've waited so others can discover all the issues first.  Now I just need DDR4 prices to come down.

[https://www.phoronix.com/scan.php?page=news_item&px=x86-PTI-EPYC-Linux-4.15-Test](https://www.phoronix.com/scan.php?page=news_item&px=x86-PTI-EPYC-Linux-4.15-Test) says there is a kernel option causing 30% performance hits. Not related to your situation, but someone might get here and could use the boot/grub option to disable the performance hit.

---

### Post by mörgæs on 2018-01-03
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by dav123456789 on 2018-01-29
Hi,

Thanks everybody, after days and days trying to make work the LTS :
Spent weeks readings, every and whole days.
Tried a LOT of different boot options.
Tried to install from both USB and DVD.
Checked everything (from the files integrity to the material itself, piece by piece, including ram, mb, bios, cpu... etc etc).
Tried to install windows to see if there was a problem on computer, worked.
Ended up trying to install 17 before trying 18. and everything worked fine at first try (more the experience i was used to with linux distrib), i'm sad for my friend she won't have an LTS and so she'll have to re install one day or another, but still, it works smoothly.

So, bad luck, but ended well, thanks everybody for the time you spent for me and the help you gave,
Dav

---

### Post by mörgæs on 2018-01-30
Good that you got it solved. 

'I only use LTS and I demand the LTS ISO to work on any given piece of hardware'-category is a frequent class of problems in Ubuntuforum. People who decide upon short- or long term support *before* testing are wasting their time - it should be an active choice in each case.

---

