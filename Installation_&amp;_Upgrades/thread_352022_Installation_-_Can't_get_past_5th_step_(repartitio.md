---
title: "Installation - Can't get past 5th step (repartitioning wizard thingy)"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by CodyZ on 2007-02-02
Problem description:
I decided to dual boot on my laptop between XP and Ubuntu, I've got a 40gb hard drive with about 13gb free space.  In windows I booted to safe mode and defragged my whole disk. Then I booted the live cd (actually it's linuxmint 2.1 bea, but it's basically 6.10 + proprietary media support), and the install wizard works fine until the 5th step, the disk repartitioning step.  There are a few options, and I chose the "resize hda1" option, and I moved the slider to indicate that I want to create a new 10gb partition.  When I hit the next button to move to step 6, the next button is grayed out and the mouse changes to the "hourglass" for a moment and then stops and the next button is no longer grayed out, but I'm still on step 5.  So I click the next button again and it gets grayed out and the mouse turns to an "hourglass" and just stays this way for hours.  The system is not frozen, as I can open other programs but the wizard just doesn't continue.  I've gone through this 3 times!  I really want to try linux, please help me out!

Questions:

1.  What's causing this?  How do I complete the installation wizard?  (and yes, I verified the MD5 before I burnt the iso)
2.  Is resizing the hda1 partition the right choice for me?  Or should I go for one of the other options, like "use largest continuous free space?"


My Hardware:

I have a Compaq Presario 2232us laptop, 1.5ghz intel processor, 40gb hard drive, and 1gb of RAM.

Thanks!

---

### Post by danielph on 2007-02-02
It doesn't sound like you are doing anything wrong. Maybe try a different approach. If you can resize the partition before you start the install with the live CD (Ubuntu or maybe Knoppix). You can just fire up gparted and resize it first then start the installer. Partition Magic is another option of course or use a text based installer for Linux.

In response to your questions 1. I sounds like a problem with the installer and 2. Yes you could try this method of largest continuous free space

---

### Post by logos34 on 2007-02-02
> Or should I go for one of the other options, like "use largest continuous free space?"

That's the next thing i'd try...If that doesn't work then chances are gparted is having problems shrinking the windows partition--maybe because there are some 'unmovable' paging/swap or hibernation files (green) at the end of the disk, or some preinstalled third-party software programs...This is a common problem with laptops.. If the former, then just go into comtrol panel>system>advanced and disble paging files, and then go to Power management and untick hibernation.  Go back to Defrag and you'll see the green bars have disappeared.   Also, run ckdsk with both error correction boxes ticked to repair any bad sectors.

Read more here:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by CodyZ on 2007-02-02
Thanks, I'll try turning off the paging files and hibernation and defrag again.  If that doesn't work then I'll try resizing using gparted, is that in knoppix?  Thank you both for the info, I'll post back and let you know how it worked out!

---

### Post by danielph on 2007-02-03
> If that doesn't work then I'll try resizing using gparted, is that in knoppix?
Gparted
Ubuntu or Knoppix will be able to run gparted (installed by default in ubuntu) from the live CD or you can download the LiveCD Gparted [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). 

QTparted
If gparted is failing you you can use qtparted which can be installed on either of the live CDs. I think it comes by default on Knoppix. 

I believe the installer uses gparted and is failing, so you may want to try qtparted.

If you are still having problems and you are using NTFS then there is always  [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

but I would try other options first

Good luck

---

