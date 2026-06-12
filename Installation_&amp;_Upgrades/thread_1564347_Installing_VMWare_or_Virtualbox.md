---
title: "Installing VMWare or Virtualbox"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by Linuxneophyte on 2010-08-30
I have been migrating my whole business from MS (sounds like a disease doesn't it), to Ubuntu. I have all of my primary and most of my secondary programs and procedures operating under Ubuntu now. It is wonderful to operate day in and day out without lock-ups, reboots and BSOD.

My challenge is, for some of my equipment there are proprietary programs that require windows to run them. So after much looking and reading I have discovered the it comes down to VMWare or Virtualbox. I have downloaded both and here is the crux of my problem:

1.) VB installed without a hitch. However when I went to us my WinXP Pro CD to install it in VB, it said "Failed! No bootable media in drive.
   So I removed the CD, rebooted the system. Started VB. Inserted the CD and then tried to install. This way the system starts to spin the CD and stops.  I know the CD is good, because I just installed my Mother-in-laws system with XP Pro using this very CD.

2.) I downloaded VM and no matter what I do from command line I cannot get VMware to install. it is "VMware-Workstation-Full-7.1.1-282343.i386.bundle" I need some assistance on which route would be the most advantageous. 

I am stumped  :confused:

---

### Post by Linuxneophyte on 2010-08-31
"Bump"

---

### Post by lechien73 on 2010-08-31
In VirtualBox, had you attached the host CD-ROM drive to your guest machine, as in the attached screenshot (CDSettings)?

Have you changed the boot order, so that the CD-ROM device appears at the top, as in the second screenshot (CDSettings2)?

Sorry if these seem obvious, but they might help us to get to the bottom of the problem. Welcome to Ubuntu, by the way :)

---

### Post by Linuxneophyte on 2010-08-31
Yes, All of these setting were set correctly. I am thinking that maybe my CD-Rom on my system is flaking out. I put the CD back in and this time it said I had a missing or corrupt file on the CD.

---

### Post by lechien73 on 2010-09-01
Quite possibly. Have you tried creating an ISO image of the CD and mounting that in VirtualBox? You can make an ISO by:

[LIST]
[*]Insert CD and allow it to mount in Ubuntu
[*]Right click on the CD and select **Copy Disc**
[*]In the *Select a disc to write to:* dropdown, choose **Image File**
[*]Then, in VirtualBox's Virtual Media Manager, add the ISO and attach it to your guest operating system.
[/LIST]

If the disc image does not create without errors, then maybe you are correct and the drive is the problem.

---

