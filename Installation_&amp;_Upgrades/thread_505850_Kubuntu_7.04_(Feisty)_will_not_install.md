---
title: "Kubuntu 7.04 (Feisty) will not install"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by chengas123 on 2007-07-20
I put in the Feisty CD today to attempt to install Kubuntu and got the message below with the last three lines basically repeating several times before the screen turned black.  Is there anything I can do?

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) [   39.953070] ata1: port failed to respond (30 secs, Status 0xd0)
[   45.978165] ata1.01 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   45.978217] ata1.01 cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in

---

### Post by overdrank on 2007-07-21
> **chengas123 said:**
> I put in the Feisty CD today to attempt to install Kubuntu and got the message below with the last three lines basically repeating several times before the screen turned black.  Is there anything I can do?

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) [   39.953070] ata1: port failed to respond (30 secs, Status 0xd0)
[   45.978165] ata1.01 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   45.978217] ata1.01 cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in

HI if you have not corrected this issue could you please give system specs and have you check the live cd for errors and if you burned the cd did you follow this "how to" on doing so.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Please post back if additional help is required. :)

---

### Post by chengas123 on 2007-07-22
Here are my specs:
ECS 945G-M3 Motherboard
G.Skill 2GB 240-pin DDR2 SDRAM 667 (PC2 5400)
Intel Pentium D 805 Processor
Albatron Nvidia Geforce 7300 GS 256MB DDR2 PCI Express x16 Video Card
SH-S162L DVD Burner
60 GB Western Digital IDE Hard Drive
500 GB Seagate SATA Hard Drive
Hauppauge PVR 500
Soundblaster X-FI Music
Syntax Olevia LT26HVX TV/Monitor connected by DVI

Thanks!

---

### Post by Pumalite on 2007-07-22
Did you follow the How-To above?

---

### Post by chengas123 on 2007-07-22
I originally used the Sonic DLA program on my IBM T60 to burn my CD.  When I chose the check CD option from the boot menu there was a blue bar in the middle of the screen and then I got the same error message I got when trying to install.  
Since you gave me the suggestions to read the CD burning help pages, I downloaded the InfraRecorder program for Windows and burned a new CD.  When I tried either checking the CD or installing, I immediately got an error telling me the CD was corrupt and to reboot (the MD5 checksum did match on the .iso).  I burned another copy of this image with my Sonic DLA program since I hadn't verified the checksum of the original CD.  I got the original error again with this third CD.  
I don't believe there's any problem with my CD because I have burned .iso files for other distros with no problem and the MD5 checksum did match.

---

### Post by Pumalite on 2007-07-22
You have to download a new iso, do md5sum, burn at 4x or less, Check for corruption before install.

---

### Post by chengas123 on 2007-07-23
I do not understand.  Why do I have to download a new .iso when the MD5 sum on the one I have matches?  I remember there being a message on the screen that said "loading kernel" at some point during the check CD process.  Isn't it quite possible I will never be able to verify the CD if Ubuntu cannot load the kernel because of this error I am getting? The MD5 sum did match after all, so that seems to be more likely to me at the moment.

---

### Post by chengas123 on 2007-07-23
I ran the CD check on my laptop and it worked.  Whatever is stopping me from installing Kubuntu on my main machine is also causing the CD check to fail.

---

### Post by overdrank on 2007-07-23
> **chengas123 said:**
> I ran the CD check on my laptop and it worked.  Whatever is stopping me from installing Kubuntu on my main machine is also causing the CD check to fail.

HI I have been searching thinking is may have been a problem with the graphics card but it seem that other have gotten the same error and this thread ( it is a long one ) may have some answer that will help you.
[http://ubuntuforums.org/showthread.php?t=415009&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3A+job+control+turned+off](http://ubuntuforums.org/showthread.php?t=415009&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3A+job+control+turned+off)
Hope you can find the solution and I will continue to search. Good luck!

Edit: this link may help also
[http://ubuntuforums.org/showthread.php?t=505040&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3A+job+control+turned+off](http://ubuntuforums.org/showthread.php?t=505040&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3A+job+control+turned+off)

---

### Post by chengas123 on 2007-07-23
I do appreciate the help.  However, after looking at the other posts you provided to me, I have decided to give up on Kubuntu at the moment.  It doesn't seem there's any clear manner in which to determine what my problem is and it may not even be solvable.  Maybe I will be back if some future version gives me better debug output.

---

