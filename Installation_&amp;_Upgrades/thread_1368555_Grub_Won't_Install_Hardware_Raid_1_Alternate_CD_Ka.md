---
title: "Grub Won't Install Hardware Raid 1 Alternate CD Karmic -- Pls. Help."
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by AlexanderDGreat on 2009-12-30
I'm using Adapted SCSI 29320 Hardware with 2 Seagate Cheetah 37gb Raid 1 Setup. 32bit Karmic Alternate-CD with partitions: /boot /swap / /home (500gb Seagate SATA).

I've searched everywhere how to get around this, but my skills would prevent me from understanding why this is happening. Can anyone pls. help me? This is the thread that I last posted in, but nobody answers yet: [http://ubuntuforums.org/showthread.php?t=1305811&page=3](http://ubuntuforums.org/showthread.php?t=1305811&page=3) They said that dmraid is not included in the alternate-cd that's why I need to install with Internet connection so GRUB will install, is that really the solution? I've tried 4 reinstalls already and quite let my life passed by and kinda weak and frustrated.


PSI used Jaunty before, and the alternate-cd worked fine. Now I fresh install Karmic, it didn't finish the installation because GRUB won't install.

---

### Post by chrisinspace on 2010-01-06
Same problem here. We're not the only ones, but no solutions:

[http://ubuntuforums.org/showthread.php?t=1353187](http://ubuntuforums.org/showthread.php?t=1353187)

[http://ubuntuforums.org/showthread.php?t=1364063](http://ubuntuforums.org/showthread.php?t=1364063)

[http://ubuntuforums.org/showthread.php?t=1323742](http://ubuntuforums.org/showthread.php?t=1323742)

---

### Post by AlexanderDGreat on 2010-01-06
Oh finally! Someone similar to my problem, I knew I'm not the only one out there. So have you tried installing Karmic with an Internet connection, that's what they say. Now that the holidays are over, I'm still stuck at Jaunty because our office needs the server, can't do anything about it now.

PS They also say to MANUALLY install grub2 and finding the partition of your Raid1. I haven't tried this yet because have no time to study and do.

---

### Post by chrisinspace on 2010-01-07
I did have an internet connection when I tried the installation.  Apt downloaded and installed components as part of the install, but no luck with the boot loader.  I should clarify, that I am having the same problem as you, but I'm using the Server disk, not the Alternate CD.

I played around a little last night with manually fixing GRUB2.  For me, it looks like the GRUB packages are actually installing, but what fails is the configuration, so the installer bombs on that step.  I tried executing the steps outlined in the link below and seemed to make some progress, but it was late so I had to give up for the night.

[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing) - Go to the 'If you messed up' section.

I have used this process before to fix GRUB on my laptop.  I dual-boot and when I upgraded Vista to Win7 it wiped out my GRUB config.  I followed these steps to fix it.  I figured this might work to build a GRUB config since it failed during the install.  After I tried it once, I rebooted and instead of getting just a black screen with a flashing cursor, I actually got to the GRUB command line that lets you troubleshoot a bad config.  I didn't have time to get any further into it, but I figure I might give this process another try to see if I can get it to work or at least attempt to use the GRUB config utility to finish the job.  

Has anyone out there successfully fixed this issue?  I could really use some pointers.  I'm not a Linux newb, but most of my experience is with desktops/laptops.  For this project, I'm trying to get Server running on an IBM x306 with integrated RAID.  I have already overcome a couple of hurdles and it really looked like this install would be successful.  I can see the array in the installer and partition/format the drive, but I just can't get the boot loader installed properly.  I don't care which one I use (GRUB, Lilo) because I'm only going to have one bootable OS on this machine.  My goal is to run Xen for virtualization.

---

### Post by AlexanderDGreat on 2010-01-07
> I did have an internet connection when I tried the installation. Apt downloaded and installed components as part of the install, but no luck with the boot loader.

Thanks for the information, you saved me some time of trying it myself.

> I'm not a Linux newb, but most of my experience is with desktops/laptops. For this project, I'm trying to get Server running on an IBM x306 with integrated RAID. I have already overcome a couple of hurdles and it really looked like this install would be successful.

Great job mate. I wish I could help you, but I've other things to do in the office so I'm stuck with Jaunty. If you will be able to fix this, can you update on this thread so I can try it as well? Thanks and good luck.

I think this is a bug.

---

### Post by chrisinspace on 2010-01-08
> **AlexanderDGreat said:**
> I think this is a bug.

I think you're right and it may even go back to Debian.  I tried to install Ubuntu 9.10 (wouldn't install boot loader), 9.04 (locked up while partitioning drives), and 8.04 (saw the mirrored pair as 2 separate drives)...they all failed.  Next, I tried Debian 5.03 and it crapped out, too.  I finally gave up on Ubuntu/Debian for this stage of my project and went with [CentOS]("http://www.centos.org/").  

I did some research on the IBM site and found out that Red Hat Enterprise Linux (RHEL) was a supported OS for this server and they even provide some drivers and documentation.  This is a home project and I didn't want to shell out for RHEL, so I decided to install CentOS, a free clone of RHEL.  It installed with no problems using the GRUB boot loader.  That tells me the problem doesn't lie with GRUB, but with the Ubuntu install.

I'll definitely make a couple of my VM's Ubuntu servers, but I guess it's good I'm being forced to work with a new distro.  I have some Fedora experience, so it's not totally alien, but I'm hoping this will help me learn some new skills.

I'm subscribed to this thread, so if you find out anything Alex, please update.  I'd love any feedback from the community, too.

---

