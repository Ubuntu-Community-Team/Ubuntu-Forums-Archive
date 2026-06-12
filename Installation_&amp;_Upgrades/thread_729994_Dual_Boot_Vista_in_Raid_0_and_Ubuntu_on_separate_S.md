---
title: "Dual Boot Vista in Raid 0 and Ubuntu on separate SATA"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by LukinLedbetter on 2008-03-20
Hello, thanks in advance for the help. I'm new to all this and want to make sure I understand what I should be doing.

I've spent a while this morning reading threads on how to dual boot Windows Vista (Raid 0) and Ubuntu (3rd drive).  However, there are a few things I'm unclear about and would like to get an answer on before I do this.  I would prefer not to have to install Windows again.

When installing Ubuntu, I will just choose the third drive and point it there.

I have 100g Sata to install it to.  I will use the 'guided' partitioning in the install so I don't have to mess with that. If I'm wrong, please let me know.

Now the thing I'm unclear about.  Where should I install grub?  I've read just let it install itself, I've read it should be put onto the MBR, I've read it should be put onto the drive I'm installing Ubuntu onto.  If it's the latter, which partition should I install it to?  I just have no clue what to do on this step.

I've read that if you don't do this part correctly you can 1) no longer access vista 2) not have a dual boot screen pop up so you can't boot into ubuntu -or- 3) screw both up.  

Can someone please clarify what I need to do so I can boot up, get a 'Choose which OS to boot' screen and have it work?

And again, I'm new so a little bit of explanation would really be appreciated.

Thanks.

---

### Post by LukinLedbetter on 2008-03-20
I've also read about some kind of program called BCD or something in Vista.  I guess you run this after installing ubuntu to the 3rd drive and it will set up your boot screen.  However, I'm still worried about where to put grub.  The last thing I want to do is not be able to get into Windows.

---

### Post by LukinLedbetter on 2008-03-20
Anyone?  Please help!  I'm eager to get it installed and learn Ubuntu!

---

### Post by LukinLedbetter on 2008-03-20
I'm sure someone out there can tell me how to do this.

---

### Post by kushykush on 2008-03-21
I am having facing similar problem.  I had Windows Vista installed on my first SATA drive (0,0) or drive C: (in Windows).  My drive (0) has two equal partitions (0 and 1).  I installed Ubuntu in the second partition (0,1) of the same SATA 1 drive.  It installed fine and also installed the GRUB.  But it must have installed GRUB in the MBR (?) most likely in 0,0 (first partition) where Windows Vista was installed.

The result is a disaster.  Vista does not boot when I make the "longhorn" selection in GRUB.   My research reveals that Vista has a new boot control (BCD) which will not allow GRUB to share the master boot.  

Surprisingly, there is no guidance available for multiboot installation where Vista is present.  I want to keep my Vista installation intact.  However, even though I have repaired Vista by using the Vista install disk and then going into bootrec.exe, Vista still does not boot.  Quite simply, Vista wants GRUB out. I hate Microsoft for that.  But it is up to us to find the right solution.

There has to be an uncomplicated solution.  After all Vista has been in the market now for more than two years.  I am disappointed that Ubuntu (as well as other Linux users) have ignored this vital issue.

We need to come up with guidance as to how to install GRUB where Vista is installed, and in a multi disk environment.  

Vice Versa:  If you install Vista after the Linux based OSs (such as Ubuntu), Vista will write its own boot (MBR) which will make GRUB disappear.

I did see a "solution" yesterday where it says you must first shrink the partition where Vista is stored and then install Ubuntu (which will also install GRUB), in the freed up space.  However, I have not tried this "solution"  I am not sure if GRUB can shrink a NFTS partition.  Even if it can, how will that help?

 This problem is specially hard for Linux newbies who do not know how to install GRUB or edit GRUB installation. Even if you did, how do you get around Vista?? There is nothing out there, because the GEEKS think you should not be using Windows to begin with.

---

### Post by Pumalite on 2008-03-21
Read All About It!!!

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
The problem is the Raid Array. Software Raid offers minimum improvement. Raid 5 is like a man with supenders and a belt.
If you insist, you have this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by confused57 on 2008-03-21
> **LukinLedbetter said:**
> Hello, thanks in advance for the help. I'm new to all this and want to make sure I understand what I should be doing.

I've spent a while this morning reading threads on how to dual boot Windows Vista (Raid 0) and Ubuntu (3rd drive).  However, there are a few things I'm unclear about and would like to get an answer on before I do this.  I would prefer not to have to install Windows again.

When installing Ubuntu, I will just choose the third drive and point it there.

I have 100g Sata to install it to.  I will use the 'guided' partitioning in the install so I don't have to mess with that. If I'm wrong, please let me know.

Now the thing I'm unclear about.  Where should I install grub?  I've read just let it install itself, I've read it should be put onto the MBR, I've read it should be put onto the drive I'm installing Ubuntu onto.  If it's the latter, which partition should I install it to?  I just have no clue what to do on this step.

I've read that if you don't do this part correctly you can 1) no longer access vista 2) not have a dual boot screen pop up so you can't boot into ubuntu -or- 3) screw both up.  

Can someone please clarify what I need to do so I can boot up, get a 'Choose which OS to boot' screen and have it work?

And again, I'm new so a little bit of explanation would really be appreciated.

Thanks.
You shouldn't have any problems installing Ubuntu to the 3rd SATA drive and have grub boot Ubuntu and Vista on your RAID.  To make sure grub gets installed on the 3rd SATA drive, set this drive as first hard drive booted in bios before you boot up the Ubuntu install cd...to insure grub gets installed to 3rd drive's mbr, click on the "Advanced" button in the lower right part of the screen, change the default (hd0) to /dev/sdc(or however this drive is designated by the partitioner)...

Another possibility is to install grub to the root partition, e.g. /dev/sdc1, then use EasyBCD to boot Ubuntu from Vista:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

I would also recommend burning a Super Grub Disk, before installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by DiabolusItalicus on 2008-03-21
Ciao guys,
I've spent just a few hours now trying to do the same type of Ubuntu installation on a 3rd SATA of a Dell XPS 420 with 2 SATA in "fake" RAID 0, thus invisible to Ubuntu, containing the original Dell installation of WVista.

After a lot of Internet browsing, I decided to have the WVista bootloader manage the whole: looks like the sole option, actually. I decided to used Ubuntu 7.10 Alternate (to avoid any issue with graphic cards or monitors) and the utility called EasyBCD to modify then the WVista bootloader.

The installation of Ububtu was a piece of cake. I just made ONE fatal mistake.

Following meaningful instructions from EasyBCD documentation, I tried to manually partition the 3rd SATA to be able to instruct Grub to get installed there, not in the MBR of the RAID 0 disks. Not knowing exactly my steps, I failed a couple of times, so I decided to switch to the Guided partitioning of the entire 3rd disk, thinking it was the same safe...

Well, it was not: to my despair, I realized the installer never asked me where to put Grub, nor I noticed any way to do so. You imagine the result: I got Grub spoiled the WVista MBR, so I had neither Ubuntu nor Vista.

I have just now finished to repair the MBR (by the way, it's an easy game: see BigM official method at [http://support.microsoft.com/kb/927392/](http://support.microsoft.com/kb/927392/)) and boot into WVista.

And I'm now asking the Forum how can I install a Grub in that 3rd SATA disk, already containing an Ubuntu that I can't boot from?

Thanks to anyone in advance, and, if there's a lesson to learn, I would say that Ubuntu:
• might want to provide more detailed instructions on manual partitioning, clearly indicating the correct sequence of partitions to create; or
• might want to improve the installation of Grub, clearly asking whether installing it in the MBR disk or in other locations.

Thanks again.

---

### Post by Pumalite on 2008-03-21
Grub installs by default to (hd0) (your Raid). When it ask you where to install Grub, you should point to the appropriate partition (/dev???) You can find out what ??? is by booting your Ubuntu Live CD and at the Terminal:
sudo fdisk -lu
Once you have accomplished that installation, you can boot your Ubuntu with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by LukinLedbetter on 2008-03-21
> **DiabolusItalicus said:**
> Ciao guys,
I've spent just a few hours now trying to do the same type of Ubuntu installation on a 3rd SATA of a Dell XPS 420 with 2 SATA in "fake" RAID 0, thus invisible to Ubuntu, containing the original Dell installation of WVista.

After a lot of Internet browsing, I decided to have the WVista bootloader manage the whole: looks like the sole option, actually. I decided to used Ubuntu 7.10 Alternate (to avoid any issue with graphic cards or monitors) and the utility called EasyBCD to modify then the WVista bootloader.

The installation of Ububtu was a piece of cake. I just made ONE fatal mistake.

Following meaningful instructions from EasyBCD documentation, I tried to manually partition the 3rd SATA to be able to instruct Grub to get installed there, not in the MBR of the RAID 0 disks. Not knowing exactly my steps, I failed a couple of times, so I decided to switch to the Guided partitioning of the entire 3rd disk, thinking it was the same safe...

Well, it was not: to my despair, I realized the installer never asked me where to put Grub, nor I noticed any way to do so. You imagine the result: I got Grub spoiled the WVista MBR, so I had neither Ubuntu nor Vista.

I have just now finished to repair the MBR (by the way, it's an easy game: see BigM official method at [http://support.microsoft.com/kb/927392/](http://support.microsoft.com/kb/927392/)) and boot into WVista.

And I'm now asking the Forum how can I install a Grub in that 3rd SATA disk, already containing an Ubuntu that I can't boot from?

Thanks to anyone in advance, and, if there's a lesson to learn, I would say that Ubuntu:
• might want to provide more detailed instructions on manual partitioning, clearly indicating the correct sequence of partitions to create; or
• might want to improve the installation of Grub, clearly asking whether installing it in the MBR disk or in other locations.

Thanks again.

It sounds like you're exactly where I'm at.  If you you point your grub installation to the 3rd drive, you say it's failing?

Or did you never get that far because you were having partitioning issues?

---

### Post by LukinLedbetter on 2008-03-21
> **Pumalite said:**
> Grub installs by default to (hd0) (your Raid). When it ask you where to install Grub, you should point to the appropriate partition (/dev???) You can find out what ??? is by booting your Ubuntu Live CD and at the Terminal:
sudo fdisk -lu
Once you have accomplished that installation, you can boot your Ubuntu with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I think this may be where a lot of my confusion lies.  I don't know the naming system for ubuntu.  

If I create  /swap, /, /home partitions when going through installation...how do I know which one of these to point the grub installation to?

if my sata is hd2...what's the difference between hd2 and /dev??? .  I'm just not getting this.

Thanks.

---

### Post by Pumalite on 2008-03-21
Boot the Ubuntu Live CD and post:
sudo fdisk -lu
I'll tell you exactly what your /dev is.

---

### Post by LukinLedbetter on 2008-03-21
> **Pumalite said:**
> Boot the Ubuntu Live CD and post:
sudo fdisk -lu
I'll tell you exactly what your /dev is.


Thanks for helping me figure out where to point it to install.  I guess my question is more for understanding...   what exactly IS /dev?  /hda?   What's the difference?

I'm sure I'm making this more complicated than it should be, but I'm really just trying to learn what these mean.

Thanks again.

---

### Post by Pumalite on 2008-03-21
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

