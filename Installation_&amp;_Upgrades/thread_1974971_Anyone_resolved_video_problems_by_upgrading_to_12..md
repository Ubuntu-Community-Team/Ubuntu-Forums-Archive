---
title: "Anyone resolved video problems by upgrading to 12.04?"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2012-05-06
Hi folks,

I've got almost nothing to lose at this point, but it wouldn't hurt to ask before investing yet more hours in something that won't work for me.

_My current system:_
Gigabyte MA-GM78-US2H motherboard, vintage 2009.
AMD 1090T CPU.
Ubuntu 11.10, 64-bit.
RAID1, administered by mdadm.
Video card was an NVidia 8800 GTS. I just upgraded to a GTX 460 card -- specifically, a Gigabyte GV-N460OC-1GI.

This system went down last month because of NVidia's recent driver bug fix, which was apparently _[meant to address a security problem]("http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc")_ and thus had to be patched to all driver revisions, new and old.  Unfortunately, the bug fix wreaked havoc with systems using somewhat older GPU's, like my 8800 GTS.

I could still run the system without a driver, but graphics were hopelessly slow for my 3-D protein visualizations.  I'm guessing that my CPU's were doing all the rendering, and the GPU's were just sitting there, inert.  I also need CUDA.

After trying for a week to get my system going again, and seeing that NVidia was not addressing the problem (although, _[they might have finally done so]("http://ubuntuforums.org/showpost.php?p=11903071&postcount=996")_, two days ago?), I thought I would try upgrading my GPU card.  That didn't work.  Now I can't boot from my hard disk at all, only from a LiveCD into a sub-optimal graphics mode.  I've spent a second week _[trying to resolve that]("http://ubuntuforums.org/showpost.php?p=11895731&postcount=992")_, with little success so far.

My son's system down the hall is running fine.  It is ALMOST identical to my system, except that his motherboard is a bit newer (Gigabyte GA-990FXA-UD5), and his GPU card is a little older (GTX 450).

My /home directory is backed up to an external drive.  So, technically, I can do anything I want from here.  But I'm tired of trying things that do not work.

I would consider upgrading to 12.04, 64-bit, IF that would help me.  _[This thread]("http://ubuntuforums.org/showthread.php?t=1960714")_ and _[this thread]("http://ubuntuforums.org/showthread.php?t=1959416")_ contain reports of some people fixing video problems by upgrading their OS -- and some people getting unsatisfactory results, sometimes even acquiring problems.  At least, it would appear that most of the people having problems in 12.04 can actually boot their machines.

I thought it might be a good idea to ask the question directly, not buried in another thread.  Did you fix your video problems by upgrading?  What were the specifics?

Thanks for your testimonials.

---

### Post by Tanker Bob on 2012-05-06
My 11.10 setup worked fine, but the nVidia 295.40 driver fiasco created havoc when I upgraded to 12.04 LTS. I manually reverted to 295.33, which resolved most of my issues, but not the incompatibility between compiz and unity. I then manually updated to 302.07 and then back to 295.49 drivers. Both sets seem to work fine on my 8800 GTS. YMMV.

However, if you upgrade to 12.04 LTS now, it will install the 295.40 driver by default. So, you'll need to manually replace it after upgrading using a text screen.

---

### Post by ladasky on 2012-05-06
Thanks, Tanker Bob.

> **Tanker Bob said:**
> However, if you upgrade to 12.04 LTS now, it will install the 295.40 driver by default. So, you'll need to manually replace it after upgrading using a text screen.

Some people are apparently getting results with 295.40.  But I have the 295.49 driver in hand, which according to several recent discussions here is NVidia's latest solution to the problems.  If I can at least get my system to boot to a text console from my hard drive, I might be able to run the installer.  Right now, I'm not even getting that far.

---

### Post by Tanker Bob on 2012-05-06
When you get to a text screen, you'll need to stop lightdm and uninstall nvidia-current, nvidia-current-updates, nvidia-config, and nvidia-config-updates before installing the 295.49 drivers. Ignore the warning that the pre-installation script failed during the driver's installation.

---

### Post by hyperreal on 2012-05-06
This may be of use to you.  I have had similar problems on 11.10 and below, but with an ATI AMD Radeon graphics card.  I bought the notebook (Samsung) in early February 2012, so it makes sense that operating systems released before that time would not come with the proper newer driver.  I installed 12.04 successfully, with no graphics issues.  However, before 12.04 was released, I was using 11.10, but I had to use the text mode install cd for Ubuntu. I installed the system to HD, booted into the recovery mode option on the GRUB menu, connected to my wireless network, and installed the proper graphics driver.  The driver that worked was in the Ubuntu repos but wasn't installed by default, so that's why I had issues with the graphical install DVD (Xorg wouldn't load, and only displayed a blank screen).

The details of the problem and a few possible solutions can be found on my blog:  [http://ellipticalclocks.wordpress.com/2012/02/28/an-alternative-route-to-getting-a-working-ubuntu-11-10-when-ati-graphics-card-fails-to-load-xorg/]("http://ellipticalclocks.wordpress.com/2012/02/28/an-alternative-route-to-getting-a-working-ubuntu-11-10-when-ati-graphics-card-fails-to-load-xorg/")

I'm not sure if that will help, but I thought I'd share it anyway.  Hope you find a solution soon.

---

### Post by ladasky on 2012-05-08
Update:

I have restored full function on my system, _[at last]("http://ubuntuforums.org/showpost.php?p=11918272&postcount=1003")_.  And I stayed with 11.10.

I detoured into 12.04 for about half a day.  Something is VERY wrong when I try to reinstall 12.04 on my system (which uses RAID1, and has ext4 partitions for root and /home).  The system hangs for minutes to HOURS on the commands **grub-install** and **update-grub**.  The hard disk access light turns on during these pauses and, mostly, stays on.  This occurred during the initial installation (which I performed using the alternate install CD), and during a repair session.  I thought that it might have something to do with rebuilding my RAID, even though I believed that there was nothing wrong with my RAID.  So I waited it out.

When I rolled back to 11.10, everything proceeded quickly.  And there was nothing wrong with my RAID.  My /home partition was in perfect condition.

This problem is tangential to my graphics issues, but it seemed prudent not to proceed.

---

### Post by NadirPoint on 2012-05-08
I run an Asus flavor of the Nvidia 460 chip.  Using the Nvidia proprietary drivers we had problems with 11.10 being very slow to come out of the screensaver and switch users, occasionally hanging and requiring a restart.  Problem seems to be cured in 12.04 after observing normal behavior for almost 4 days now.

I see no common denominator.  :confused:

---

