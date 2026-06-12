---
title: "Cannot dual boot XP Pro+Ubuntu"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by Jori on 2007-07-29
Hello.  Im currently trying to run my system (specs below) off of Ubuntu Studio and Windows XP Pro.  I installed Ubuntu onto a 40 gig IDE drive with a 38.5 gig partition for the OS, 1.3 gig for the "swap" and around 200mb's for the grub loader thing.  Now, being completely new to Linux I dont know what I am doing really, just figured this would be about right.  Now, the BIOS detects that I have a 40 gig IDE (Linux) 80 gig SATA (Windows) and a 160 gig SATA (Storage).  When I change the boot order to boot off the 40 gig, with the 80 gig on secondary priority, it just boots Windows.  Then, in Windows it doesnt not even show the 40 gig.  I have disconnected all hard drives except the 40 but it said to put in a system disk or something to that effect.  Specs are

AMD 3600+ X2
Biostar TForce 550
7600GT
2 Gig's Corsair DDR2
80 Gig SATA, 160 gig SATA, 40 gig IDE

---

### Post by DC@DR on 2007-07-29
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236) -> This is a video which shows you how to setup a dualboot system (XP and Ubuntu). Take a look to see if you find smth you did wrong with your system :-)

---

### Post by dabl on 2007-07-29
> **Jori said:**
>   I installed Ubuntu onto a 40 gig IDE drive with a 38.5 gig partition for the OS, 1.3 gig for the "swap" and around 200mb's for the grub loader thing. 

No -- that won't go.

1. Download and burn a GParted Live CD, and use that to do the partitioning and set the boot flag.  [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

2. The most "natural" approach, for both Win XP and Ubuntu, is to install your WinXP first, on the first hard drive in your system, and let Win XP set the Master Boot Record (MBR) in the first partition on that first hard drive,  Then Ubuntu will happily install itself where you tell it to, install Grub alongside the Win booter, and make a boot menu for you that lets you choose what to boot.

3. Assuming that 40GB IDE drive is a second drive, and all for Linux, then boot your GParted Live CD and make 3 partitions as follows:

a. 8GB (this will be for "/", set the "boot" flag on this one)
b. 500MB (this will be for swap)
c. all the rest of it (this will be for "/home", for your data)

Use "apply" in GParted to set your partions, and then exit out of GParted and reboot, this time with the Ubuntu Alternate Install CD.

4. With the Alternate Install CD, you will have a VGA/text mode installer.  Follow "guided partitioning", select the partitions and mount points as indicated above, let it format them, and then let it place Grub where it wants, which will be on the MBR where Win XP lives.  When you're finished, reboot and you should get a boot menu that will give you a short while to choose your OS, and then proceed to boot Ubuntu if you don't tell it to boot Windows.

:)

---

### Post by Jori on 2007-07-29
So wait, I have to do a clean install of XP?

---

### Post by MQMike on 2007-07-29
I think you want to boot off the SATA Windows drive, not the 40 GB Linux drive.  (Windows was already there first, right?)
When you installed Linux, it may have overwritten the MBR of the SATA drive with GRUB (which is OK).
So, in BIOS, if I get you right, the boot order should be 
CD/DVD drive
SATA Windows second
40 GB Linux third


(You MAY have to re-install GRUB to the MBR of that SATA Windows drive—see the How-To’s)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

(I would agree with you, you don't want to have to re-install XP.)

---

### Post by dabl on 2007-07-29
> **Jori said:**
> So wait, I have to do a clean install of XP?

Nope, sorry, didn't mean to say you had to do a new Windows install if it's already installed and working fine.  I couldn't tell whether you meant to "start over" with your whole system, and wanted to make sure you were clear that it's Windows first, Ubuntu second, if you want to maintain low blood pressure.

:)

---

