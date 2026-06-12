---
title: "Grub Problem with Ubuntu Studion 7.10"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Wolf011358 on 2007-11-14
I am new to Ubuntu Studio 7.10.  I installed it this morning.  Things went fine, after doing a manual partitioning, since I have an external harddrive sda.  I gave Studio 70gigs on that disk with a 2gig swap.
The problem is, I have my sda drive as a mirror for my XP install, so when it installed grub for a dual boot, it installed it onto the sda drive and not the hda drive.  So, I can't boot into Ubuntu Studio for now.  How do I get Grub to be installed on my hda drive so I can see my Ubuntu Studio on my sda drive?  It is connected by 1394 firewire, if that makes a difference.

Please keep in mind, I do know a lot about building computers, but I am a novice when it comes to doing things like command line interfaces and such.  So, if you suggest running any scripts or such, please be specific about the script.  

I'm sure that one can go back in and have Grub install on a different hard drive, right?  Just need to know how.  

Thanks in advance everyone.  Ubuntu looks great!  

HP Pavillion AMD 2600
120gig hard drive (main)
120 gig hard drive (1394 firewire external with Ubuntu on it)
756 megs ram
XP Home Edition with Mirror on sda sitting alongside Ubuntu
Nvidia 5200 Ultra video card


Oh, one last question.  Any suggestions for a professional DVD authoring package for Ubuntu, or as close to professional as possible?

Thanks again.

The Wolf:)

---

### Post by Wolf011358 on 2007-11-16
Okay, after doing some reading, I saw where I can erinstall Grub or Lilo using the cd.  I went through the process using the rescue a broken system.  But it asked me where I wanted the boot file loader to be placed.  It only gave me hda1 hda2.  Not sda1.  Do I want it to install itself on hda1?  Or will that kill my XP side?

Thanks
The Wolf:)

---

