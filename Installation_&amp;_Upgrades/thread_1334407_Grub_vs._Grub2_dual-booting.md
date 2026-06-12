---
title: "Grub vs. Grub2 dual-booting"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by timzak on 2009-11-22
I currently have a laptop with Windows Vista and Ubuntu 9.04 set up to dual boot.  Vista is almost never used, but kept on there in case a Windows system is ever needed.

I've heard that there are some differences in how Grub2 sets up on a dual-boot system, vs. Grub1.  Is there anything special, or different from Grub1/Jaunty that I should be aware of prior to starting the install process on Karmic?  I don't want to upgrade, I want a fresh install of Karmic.

My normal sequence of events:
1) back up everything off of the Jaunty install.
2) boot up with the Karmic install CD and wipe out all the Jaunty partitions (I want to do this to reorganize some of the Ubuntu partition sizes anyway).
3) install Karmic from scratch with fresh partition setup (leaving Vista partitions alone, of course).
4) hope Grub2 set up dual-booting properly?

Currently, with Jaunty, Grub boots to a menu that allows me to choose Ubuntu (default) or Vista.  Can I also expect this in Karmic?

I had an issue on my desktop with Grub2 being installed on the wrong partition (I installed Karmic on sdb and grub2 was installed on sda).  My understanding is this is a bug.  Hence my apprehension with this install.

Thanks,
Tim

---

### Post by oldfred on 2009-11-22
I believe Grub2 is better at finding other systems and adding them to the new grub.cfg file. There still are exceptions of course.

When I installed alpha it gave me a choice where to install grub. I just installed from the liveCD and I would swear I never got to click the advanced button to choose where to install it. It installed to the drive it considers to be first. I have seen enough users where fro some systems that is not the true first drive.

I have also seem issues with old grub, BIOS, windows, and Ubuntu not agreeing on drives and drive order. New grub seems slightly worse. One user said both windows and Ubuntu saw his 2nd drive but grub2 did not. It turned out to be a setting in BIOS that windows and Ubuntu bypassed but Grub2 did not.

Choose manual install, so you can tell it to overwrite or reformat your old Jaunty partition and reuse your current swap.

---

### Post by drs305 on 2009-11-22
> **timzak said:**
> 
My normal sequence of events:
1) back up everything off of the Jaunty install.
2) boot up with the Karmic install CD and wipe out all the Jaunty partitions (I want to do this to reorganize some of the Ubuntu partition sizes anyway).
3) install Karmic from scratch with fresh partition setup (leaving Vista partitions alone, of course).
4) hope Grub2 set up dual-booting properly?

Currently, with Jaunty, Grub boots to a menu that allows me to choose Ubuntu (default) or Vista.  Can I also expect this in Karmic?


This is how Grub 2 should work, and does for most users. One follow-up action that might be necessary is to run "sudo update-grub" if Grub 2 failed to see the Windows partition on the initial install. In most cases, if it doesn't see it initially it will once you run the update.

---

### Post by timzak on 2009-11-22
Thank you for the replies.  I think I'll be able to do this upgrade over the long weekend, so I'll come back if there are any issues.

I appreciate the help and advice!

---

