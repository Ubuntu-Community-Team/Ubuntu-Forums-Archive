---
title: "installation problems"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by jlehn on 2007-07-26
Hello All,

I am trying to install Ubuntu Desktop 7.04 on my machine for a test project.  For the most part everything seems to work well.  However, when I start the install process i can get all the way to the partitioning tool and then everything falls apart.  In the partitioning tool it does not show any of my disks (i actually only have one disk).  The funny thing is i know that the disk is there and that the disk is not bad because i can still boot into windows.  I really need to get this up and running, it is the only spare machine that I have to install Ubuntu on.  The machine specs are as follows:
    IBM ThinkCentre A50p (8194-A4U)
    120 gig Western Digital
    9600 ATI 256 meg graphics card (from Asus, internal video is disabled)
    3COM gigabyte nic (internet nic is disabled)
    2 gigs of ram
    1 old CD-RW from HP

Please help.

---

### Post by reckless2k2 on 2007-07-26
yeah you need a dual boot if you have windows currently on it and you don't want to kill windows. you'll have to  defrag windows and then free up a partition space to install linux. if i'm speaking french, query dual boot in these forums.

---

### Post by dabl on 2007-07-26
You might have better luck booting a GParted Live CD to use for the drive partitioning. It's on Sourceforge.

But do a Disk Clean followed by a Defrag in Win XP first.  Then boot the GParted Live CD and shrink the XP partition, so that you free up at least 15GB for Ubuntu.

Then boot your Ubuntu Alternate Install CD, which will run in text/VGA mode, and give you lots of control over the process.

:)

---

### Post by jlehn on 2007-07-26
I am very comfortable with dual boot systems; however, that is not the problem.  I do not need to dual boot this system.  This system will not have windows on it after this (provided that we can get it to work).  The problem that seems to be happening is that when you try and load the disk (desktop or alternative) it either does not see the harddrive at all or it asks for a driver for the disk drive.  Also when starting the desktop cd it takes you to busybox and give the message 

initramfs
[  168.704319]  ATA1: port failed to respond (30 sec, status 0xd0)

I take this to mean that it can not read the harddrive.  If you wait it does eventually load the GUI for Ubuntu but when you go to the installer and start to work through it, you can work until you have to partition the drive.  At this point it does not show any devices in the partition tool.  I know this harddrive works and I have now tried it with two different disks and neither one works.

---

### Post by davidjmayo on 2007-07-26
Have you verified the download was Ok with MD5sum and burned correctly?

see here [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by jlehn on 2007-07-26
md5 check sums are all ok.

---

### Post by Pumalite on 2007-07-26
Have you checked your BIOS for IDE Configuration? Do you have such an option? If so, then Make sure Advanced Support for PATA+SATA are enabled.

---

### Post by jlehn on 2007-07-26
I have checked the bios settings.  Support for both PATA and SATA is enabled and just as an added bonus all the drives are regular PATA or IDE as it be.  I am going to try and disable the SATA portion of this since i do not have any.  If you have any suggestions i can try it again when i get to work tomorrow.

---

### Post by Pumalite on 2007-07-26
It's better to leave it at PATA+SATA. It won't hurt.

---

### Post by jlehn on 2007-07-27
thats fine and all but it does not work and i currently have no idea as to why.

---

### Post by Pumalite on 2007-07-27
If you are planning to get rid of windblows anyway, why don't you go for broke?. Use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/) followed by Gparted as dabl suggested, and then install. It might erase anything windblows related that might be impeding you from install. Before you do it; do one last thing: change your IDE conf from Auto to LBA and try again.

---

### Post by jlehn on 2007-07-27
I already setup the BIOS to ide only and disabled the SATA portion of the controller.  I have not tried the DABL tool however i have tried two western digital drive and neither of them worked.  I am currently trying the install with a hitachi drive which seems to be working for now but i need that drive back so this is only a temporary solution.  If i remember correctly from yesterday when i did the alternate install it asked me for a disk driver for the device (the harddrive) which of course i could not find.  If there is a specific driver i need to use Western Digital please let me know.  I don't remember having this problem on any of my systems at home.  

Please help.

---

### Post by Pumalite on 2007-07-27
You should listen to dabl and get the bootable Live CD of Gparted. It's the best partitioner around and can also help you detect your drive.

---

### Post by mistafreeze on 2007-08-27
The guy is not wanting to dual boot, he has no need to re-partition his harddrive.

He also has no need to wipe the drive with dban.

He has a problem recognizing the WD harddrive, meaning it cannot be read.

I havn't used ubuntu in a long time, but I am about to buy the same machine this guy has and was checking for linux compatibility problems and stumbled upon this.

It seems your problem lies in the WD harddrive.  Have you given ubuntu a long enough time to check your harddrive?  

I installed ubuntu on a test machine and it took well over 10 minutes for it to read my harddrive.  I too thought it had failed but it did not.


Last but not least, have you installed any other linux distros on this machine?  Have you had any other problems getting them to work?  Since you can get your Hitachi to work, the installer is probably having a problem detecting the drive, you may need to give it some time.  But the good news is it is not the motherboard, nor the bios, as if it were it would be unable to detect the hitachi.

Please respond at your earliest convenience.

---

