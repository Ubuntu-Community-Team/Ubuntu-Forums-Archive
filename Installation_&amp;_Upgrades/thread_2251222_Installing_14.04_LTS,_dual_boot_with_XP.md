---
title: "Installing 14.04 LTS, dual boot with XP"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by jrosado on 2014-11-02
I need help installing 14.04LTS.

I've found that I need to keep XP, as there are a few programs I occasionally need that won't run of any later versions of Windows.  Otherwise I would simply reformat the drive and install 14.04 from scratch.

I looked at these pages. I will carefully peruse these two:
Upgrade to 12.04 : [https://wiki.ubuntu.com/PrecisePango...untu_12.04_LTS]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS")
Install 14.04 : [https://help.ubuntu.com/14.04/instal...ide/index.html]("https://help.ubuntu.com/14.04/installation-guide/index.html")

I'd appreciate your advice in installing 14.04 while keeping XP intact.

---

### Post by Bucky Ball on 2014-11-02
Might be an idea to, while in XP, open up disk management and take a screenshot of the set up of the disk you are intended to install Ubuntu to. That will give us some clues for a plan.

If you want to install next to XP, my method would be to choose 'Something Else' when you get to the partitioning section and partition manually. You might want to have a look [HERE]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"), but let's have a look at what you already have first.

PS: Attach the screenshot by clicking Adv Reply and using the paperclip icon. Thanks.

---

### Post by grahammechanical on 2014-11-02
You should also tell us the specifications of your machine and include the graphic adapter and the amount of memory that the graphic adapter has. You may need to install a flavour of Ubuntu instead of Ubuntu if your graphic adapter cannot do 3D accelerated graphics.

By the way, the first of those links only applies if you have Ubuntu 10.04 installed. Do you? All this is important information.

Regards

---

### Post by jrosado on 2014-11-02
My XP version doesn't want to screen capture, so I took a photo with my iPad:

[ATTACH=CONFIG]257716[/ATTACH]

Hope that will do.

---

### Post by Bucky Ball on 2014-11-02
Ok, you have no unallocated space to install Ubuntu. Unless you are running UEFI you are limited to four partitions per hard drive so you are going to need to shrink the NTFS Windows install to make some. If you delete that 'unknown partition' which probably contains not much (very small) you will then have three partitions. Shrink the Windows partition and create an extended partition in the unallocated space. We'll get to that, but for the moment, delete the small partition and shrink Windows.

What is the 'unknown' 10Gb partition? Anything on it?

I am presuming the specs of this machine aren't that great. I advise using Xubuntu or Lubuntu which are less resource hungry and won't take as much room on the hard drive. (I use a minimal install with Xubuntu's desktop environment xfce4, but that might be a bit down the track. ;))

---

### Post by jrosado on 2014-11-03
The first partition is Sony's XP reinstall.  It's got the earliest version of XP and all the bloatware they ship with the laptop.
The second partition (10.68 GB) and the third partition (958 MB) were created when I installed Xubuntu.
The last partition is XP, servicepack3 + security updates and all the apps and data accumulated over the years.

I don't use this laptop much.  Before I got my iPad, I used it for a backup for mail and internet when my desktop wasn't behaving and for the programs that wouldn't run on later Windows versions.  I still need those occasionally. 

When I originally tried to install Ubuntu,  the machine wasn't adequate; but Xubuntu worked fine.  I assume that will be the case now.

If I delete  partitions 2 and 3, will I be able to boot into XP and then install the latest Xubuntu?

---

