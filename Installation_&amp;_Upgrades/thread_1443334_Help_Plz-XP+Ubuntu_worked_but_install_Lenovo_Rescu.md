---
title: "Help Plz-XP+Ubuntu worked but install Lenovo Rescue &amp; Recovery = can't boot anywhere"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by kghastie on 2010-03-30
Aaargh.  I'm pretty new to Ubuntu, and tried to add a dual-boot install to my Win installation on my work laptop (Lenovo T500, downgraded to XP SP3).  Installed Karmic successfully, and I was able to boot via Grub 1.974 beta (I think that's the version).

However, I just now started to install Lenovo's Rescue & Recovery program.  It asked me to restart, and now I just get a screen that says:

GRUB

And nothing else happens.  No F keys do anthing, and the ThinkVantage key does nothing unless I press it at the beginning + F1 to get to the BIOS settings.

Can anyone help me?  I have been googling, but the stuff is so far beyond my experience with MBRs and Grub and the R&R hidden partition that I am afraid I'll do more damage if I try anything.

My order of preference are as follows (since this is my work laptop, and I really need to get to a working state in one OS by tomorrow a.m.):

1) Boot into the existing XP OS successfully, in any way.
2) Be able to boot into the existing Ubuntu installation
3) Be able to run the R&R alongside my dual-boot installation
4) Default to XP for now (during an unattended restart)

#1 is the biggie.  Here is my GParted info from running a LiveCD:

```

/dev/sda             149.05 GB

/dev/sda1   ntfs       50.00GB boot-flagged
/dev/sda1   extended   99.05GB no flags
  /dev/sda5 ext4       94.98GB no flags
  /dev/sda6 linux-swap  4.07GB no flags

```

I assume that my sysadmin wiped the initial Vista R&R hidden partition, but I might be wrong.

Any assistance would be HUGE - thanks in advance!  If you can walk me through some steps, I'll try to be responsive over the next few hours.  Otherwise even a link to the most appropriate forum posts or external pages would help...

---

### Post by kghastie on 2010-03-31
BTW I have access to the following boot discs, if that helps:

Win:
- Ultimate Boot CD v4.1.1
- OLTPE Recovery Disk from Bleeping Computer
 - Lenovo Hard Drive Disk Test 5.1.542707
- Some kind of image of the drive, although it is not a working set of Recovery Discs. The 2 Win XP CDs with SP2 or 3 slipstreamed in BSOD on me when I try to load the Recovery Module

Linux:
 - Karmic Koala 9.10 64-bit AMD LiveCD
 - Knoppix 6.2.1

Ah, I finally got into Recovery Console with the "correct" Win XP disc from work (my sysadmin made it from his base XP SP3 install).  

It asks me to boot into

1: C:\minint
2: C:\WINDOWS

I am guessing I should be running fixboot and/or fixmbr, but I'm afraid I'll screw something up worse if I proceed any further...

---

### Post by kghastie on 2010-03-31
Sorry if I should have put this in the noobs forum.  I got confused by the Beginner Talk archive and so posted here instead.

So I am wanting to use the instructions here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows), but I'm not sure which option to go with.

I did an install of 9.10 64-bit so I should have Grub 2 (although I remember it saying something about 1.974 beta).  Is that "Grub 2" or "Grub Legacy"?  I'm not sure how I could have ended up with Legacy since it was a fresh install from the 9.10 LiveCD.
  
 Here is my old fstab from /etc on the linux partition:
 

 ```


# <file system> 				<mount point>   <type>  	<options>       		<dump>  <pass>

proc            				/proc           proc    	defaults        		0       0

# / was on /dev/sda5 during installation
UUID=91f8145a-019c-483a-b471-a5e2cb8e16fb 	/               ext4    	errors=remount-ro 		0       1

# swap was on /dev/sda6 during installation
UUID=ab66a6b3-a06b-4de7-8d8e-7ac1e042449c 	none            swap    	sw              		0       0

/dev/scd0       				/media/cdrom0   udf,iso9660 	user,noauto,exec,utf8 		0       0
/dev/sda1 					/media/winxp 	ntfs-3g 	defaults,locale=en_US.UTF-8 	0 	0[FONT=Verdana]
[/FONT]
``` 
Is there a technique I can use that will allow me to complete the R&R setup and use recovery CDs?  More importantly for now, what is the safest way to get back into either environment (preferably Windows)?  
 Thanks!

---

### Post by kghastie on 2010-03-31
Moved to noob forum and resolved:

[http://ubuntuforums.org/showpost.php?p=9055054&postcount=2](http://ubuntuforums.org/showpost.php?p=9055054&postcount=2)

---

