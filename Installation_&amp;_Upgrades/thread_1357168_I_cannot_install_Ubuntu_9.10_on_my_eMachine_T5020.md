---
title: "I cannot install Ubuntu 9.10 on my eMachine T5020"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by ctsutherland on 2009-12-16
Hello,
 
I'm sorry if this is already posted somewhere but everything I've been able to find hasn't resolved my issue.
 
Here's what I've got:
 
eMachine T5020
Intel Pentium 4 Processor 519
160gb Sata HDD
1gb RAM
DVD R/W
 
When I start the PC with the Ubuntu 9.10 disk in the CD ROM it kicks off the Ubuntu installation. I select "English" and then "Install Ubuntu".
 
At this point I get the black screen with the white circle & dots for quite some time before it times out and then I get the following:
 
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
mount: mounting /dev/sr0 on /cdrom failed: invalid argument
mount: mounting /dev/sdb1 on /cdrom failed: invalid argument
/init: Line 1: can't open /dev/ssc: No Medium Found
/init: Line 1: can't open /dev/ssc: No Medium Found
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
mount: mounting /dev/sr0 on /cdrom failed: invalid argument
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu-7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system
 
I have tried another DVD ROM, HDD neither resolved. I replaced my video card with another, did not resolve.
 
I have tried booting to USB and all I get is "Boot Error" when I boot to my USB. I have used the Unetbootin program to create my USB image 3-4 times. This did not work either.
 
Does anyone have any idea(s) what I can do to get Ubuntu installed?
 
You help is greatly appreciated!

---

### Post by Sef on 2009-12-17
Instead of installing, go down to 'Check Disk for Errors' (or something similar.)   Make sure that the disk and the burn/download are good.

---

### Post by ctsutherland on 2009-12-17
Sef, 
 
Thanks for the thought. My apologies however as I forgot to mention that I was able to install Ubuntu 9.10 using the same disk on a much older PC, however this PC is not mine. I'm just repairing it for someone else.
 
Note: This "older" PC is a barebone that I built a while back. It has an IDE HDD in it whereas the eMachine I am trying to install on has a SATA HDD.
 
Thanks,
Chad

---

### Post by sterilegenie on 2009-12-19
Ihave the same issue trying to boot the live cd on my Compaq Presario sr1603wm. I can boot any previous version of (K)(X) (U) buntu but not this latest release, must be something screwy with udev? Do you have a card reader in your machine and have you tried disabling it and booting up again?

---

### Post by jrod2315 on 2010-01-09
> **sterilegenie said:**
> Ihave the same issue trying to boot the live cd on my Compaq Presario sr1603wm. I can boot any previous version of (K)(X) (U) buntu but not this latest release, must be something screwy with udev? Do you have a card reader in your machine and have you tried disabling it and booting up again?



i have the same problem but i have use ubuntu in the same computer i have a compaq presario sr1603 2gb amd athlon 64 dual core  and 500 gb hard drive sata  and is not the disk because i have use the disk on other computers and it work fine this is the message i get

/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
mount: mounting /dev/sr0 on /cdrom failed: invalid argument
mount: mounting /dev/sdb1 on /cdrom failed: invalid argument
/init: Line 1: can't open /dev/ssc: No Medium Found
/init: Line 1: can't open /dev/ssc: No Medium Found
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/ssd: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/sse: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
/init: Line 1: can't open /dev/ssf: No Medium Found
mount: mounting /dev/sr0 on /cdrom failed: invalid argument
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu-7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system


please can somebody help me thanks

---

### Post by moodog on 2010-02-01
Has anyone found a solution for this? I am trying to install mythbuntu, and select the Install option, and end up with the mythbuntu logo on screen, followed by the flashing '_'. When I press ctrl-c I just see similar to the following repeated many times:
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found


I haven't left it go forever to see if it ends up with the same error message. Unfortunately the motherboard only supports "boot from USB CD/DVD, boot from USB Zip" - not boot from USB memory stick....

---

