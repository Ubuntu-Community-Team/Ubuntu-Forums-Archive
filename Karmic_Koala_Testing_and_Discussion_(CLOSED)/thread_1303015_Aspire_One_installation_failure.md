---
title: "Aspire One installation failure"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SaintStewart on 2009-10-27
I have been trying for hours now to get 9.10 installed on my ZG5, and I am at a loss as to what is going on.  I get an error that says my media fails...well, I will just repost from my unanswered post from [here:]("http://ubuntuforums.org/showthread.php?t=1302899")

> Hi all. Im on an Aspire One (ZG5). Im trying to install 9.10RC on this thing, but every time I get to the same point in the install then failure. I get:

[Errno 5]: Input/Output Error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.


...thats nice. I know for a fact its not the machine, as I have Win7 on another partition, and it is working fine. I have redownloaded the RC ISO three times now, to be on the safe side, as well as burnt the ISO to two different CDs on two separate machines, and have also used UNetbootin to load the ISO to a 5GB USB drive. They all fail at the same point, which leads me to beleive that perhaps there is a problem with the ISO. Perhaps. Has anyone else had this problem? Pretty frustrating as I was looking forward to trying out this generation of Ubuntu. 

Hopefully someone else out there is having a problem like this, or can tell me what to do. If you need any more info, please let me know. Ill be monitoring the thread.

Thanks in advance.

Acer Aspire One (ZG5)
1.6GHZ Intel Atom
1.5GB RAM
160GB HD



So, on top of all that, I have even downloaded the 'alternate' install CD and it fails too.  Everything goes fine up until 36%, then fails with that error message.  I have switched out multiple drives connected externally, and as stated above, have downloaded the ISO multiple times.  Not sure whats going on, but I am getting really frustrated.  Any help would be really appreciated.  Thanks.

---

### Post by flipper9 on 2009-10-27
Assuming it's not an incompatibility between Karmic and your hardware causing the failure, have you tried using Unetbootin for Windows and a USB Key (1gb sized key or larger, really cheap nowadays)?  

You can fire up Unetbootin in Windows, select Ubuntu Karmic Latest (or browse for the already downloaded ISO file on your PC), have it download and setup the USB key to be able to boot on your system, then install from the USB Key?

Assumptions: you have a USB key, your system can boot from a USB key (check the bios, or maybe select boot media when the system boots up, sometimes hit ESC key, F-10, F-12...see bios message or bios settings)

---

### Post by SaintStewart on 2009-10-27
> **flipper9 said:**
> Assuming it's not an incompatibility between Karmic and your hardware causing the failure, have you tried using Unetbootin for Windows and a USB Key (1gb sized key or larger, really cheap nowadays)?

As above, yes, I tried that too...thanks though.  :)

OK: NOTE: I dont know if it is a bug or not, but I cannot install normally using any CD, *BUT*, on the normal i386 install CD, if I choose "Install" rather than "Boot from CD" it installs fine.  I have confirmed this twice now.  I can install 9.10 on my ZG5 fine if I just choose the plain "Install" option, but not any other way.  Not even from the "alternate install" CD. 

Is there a reason for this?  What could be wrong with my machine (if anything...any other distro installs fine, so does 9.04)?  Is this a bug in 9.10? Ideas?  Comments?

---

### Post by flipper9 on 2009-10-27
I had that happen on a machine with Jaunty.  Not sure what the problem was, but I was able to install just fine...just couldn't run the Live CD.  I didn't really care at the time as my goal was to get the OS installed, not try it out.

---

### Post by tahina on 2009-10-28
I have an ZG5 (aka something-something-150). 

I'll try installing from running live-cd (usb) and see what happens...

---

### Post by tahina on 2009-10-28
Okeli-dokeli. That went smoothly. I installed the daily-live image of the 27:th. No problems. And when I posted the last post, the image hadn't even downloaded yet.

---

