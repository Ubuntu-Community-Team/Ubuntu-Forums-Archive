---
title: "[SOLVED] Ubuntu will not install"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2006-10-09
I have had Ubuntu 6.06 for about 2 months now and I am having a lot of trouble. I bought and assembled a new machine to run Ubuntu. The machine ran fine in the beginning and I installed Ubuntu. Ubuntu ran smooth for about a month and then I started noticing problems. For instance it would not boot past "Mounting root file system". 

  When Ubuntu was running fine I decided to try to install drivers for a Wireless network adapter (WUSB54G), to no avail. The problems with Ubuntu booting started after I ran a 'make' command trying to install the drivers. I think something might have become screwed up because the 'make' command output some errors. 

  I then tried to reinstall Ubuntu. I used a DOS boot disk to reformat the hard drive and then I deleted all the partitions. When I viewed the partition information there was none defined. I then tried to boot to the Ubuntu Live CD and nothing happened. I keep getting to a screen that says Verifying DMI pool data... and under that it says GRUB loading please wait... and then I get Error 22. 

 I basically have no idea what I am doing so can someone please help me. I just want to reistall a clean version of Ubuntu onto my hard drive. It does not dual boot to anything else it is just Ubuntu. Thanks and sorry for the lengthy story I just want to get it up and running so I can test it out.

---

### Post by encompass on 2006-10-09
Sounds like something outside of Ubuntu may be causing the problem.
IF your trying to run the live CD now and it doesn't work, when it worked before... something else, outside of ubuntu had changed.  Perhaps some of your new hardware has got problems.  I had that with my new harddrive that is getting fixed under wauranty.  GRR, still haven't got it back yet.
Doing what you did should not have interfered with your bootup.  IF anything you should be able to select an older kernel that is installed and run from there.  Can you do that?

---

### Post by lemonsCC on 2006-10-09
Why did you use a DOS boot disk to format?  You can use GParted on the liveCD (or so I hear) and format the drive, set your partitions, etc.

---

### Post by JawsThemeSwimming428 on 2006-10-09
I can't used GParted because I can't boot to the Live CD. I don't think it is a hardware problem because the system worked like 2 days ago and I changed nothing since then (except for adding a floppy drive so I could boot to DOS and delete the partitions and format). I tried using Smart Boot Manager but I could not create the disk because I couldn't get RawWrite to work. Any other options or ideas? Thanks for the quick reply.

---

### Post by paulmac on 2007-10-08
I too am having very strange problems installing Ubuntu (again).  I have tried 7.4, Gutsy, and 6.10.  I have tried two different motherboards with no luck.  It is odd because I also in the midst of all this also installed Xp with no problems at all.

What happens is the live CD will start to boot up and then the progress bar just halts on Gutsy and 7.4.  With 6.10 the progress bar has these strange saw tooth patterns about the last 1/3 of the bar and like the other two versions just halts.

I had 7.4 running on this machine before with no problems.  

It is a puzzle to me why Xp will load with no problems but now with Ubuntu I can't even load the live CD.  Strange.

The is a 64 bit system with a MSI Nvidia card.  Nothing else is on the disk but Windows which works perfectly.  

I have been using Ubuntu for a couple of years.  Have downloaded new install disks with no good results.

Any ideas?

---

