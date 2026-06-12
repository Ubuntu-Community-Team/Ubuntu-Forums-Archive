---
title: "Can Ubuntu be INSTALLED on SATA RAID0?  yes or no?"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by snoochems on 2005-08-01
Hi all.
I'm new to linux.  
I decided that i might take my first step and investigate this alternative to windows.

But, i only have 2 HDD's, and they're in a stripped array.  I'm have no intentions what so ever to take them out of the array.  

So, if Ubuntu can not be installed on a RAID0 drive, then i will not bother proceeding.

SO, CAN UBUNTU BE INSTALLED ON A SATA RAID0 DRIVE?

Yes - awesome, then that's that.  I'm in.  Is it a simple process?

No - well, what linux distro's are there that can be installed?



Additional info:
System:
AMD64 3200+
Abit AV8 mobo
1 GB RAM
2x WD SATA 120GB 8MB cache HDD in stripped array
VIA 8327 RAID controller.
Will also want to run Windows XP x64 in dual boot.
Require RAID0 for my video editing i do.

---

### Post by kosmic on 2005-08-01
Ok, First... To install your RAID system in windows it was needed drivers ? if yes, then you can't install ubuntu in that raid system in a simple way :(

If you want a trouble free distro that can run and install in RAID system give a shot to Fedora.

If you are decided to install ubuntu, then you can try to partition that drive in windows with (Partition Magic), and format the new partition in ext3 or ext2 then boot ubuntu and Ubuntu will see that partition and install trouble free :)

---

### Post by snoochems on 2005-08-01
I'm not worried about 'ruining' my windows install.  

I'm done plenty of dual boots before, and back up regularly, and, now i think about it, i reinstall windows regularly too.

I just want to know if it is possible to install ubuntu on a RAID drive

---

### Post by mingus on 2005-08-01
[QUOTE=snoochems]I'm not worried about 'ruining' my windows install.  

I'm done plenty of dual boots before, and back up regularly, and, now i think about it, i reinstall windows regularly too.

I just want to know if it is possible to install ubuntu on a RAID drive[/QUOTE]

Sorry, but it is just not that simple.  RAID is implemented in different ways; there is hardware RAID, software RAID, and the hybrids (like Promise cards).  The reason kosmic asked if you needed to install W$ drivers to activate the RAID functionality is because that would mean you are using a software RAID and there may not be equiv drivers avail in Linux.  In contrast, Linux (like XP) handles hardware RAID no problem because there is a completely separate controller which manages it.  There can be additional complications, for example, I have a dual-function IDE/RAID controller on the mobo but the RAID needs an additional software driver and if RAID is used, the drive on this controller is not recognized by the BIOS for boot - by either Linux or W$.

Therefore, to get your answer, you need to search for the particular type of RAID you have.  If it is like mine, even though on a popular mobo, you may still not find an answer specific to your rig - but if you understand *how* yours works you will probably be able to decipher an answer from similar configurations.

---

### Post by snoochems on 2005-08-01
It's 'motherboard' RAID.  Yes, it needs those damned 'press-F6' drivers for winblows to be installed on the array.

The RAID controller is a VIA 8237.  

Now, i haven't heard any "no's" so far.  I can probably handle the 'not in a simple way'.  

So, where do i find out if i can or not.

I'm downloading the image as i type.  tommorow, i'll burn it, and then chuck it in.

What should i expect if i want it to install on my the stripped array?

---

### Post by mingus on 2005-08-01
I did a bit of googling, and I'm afraid you'll need to do the same . . . from the pages I found, looks like it can be done.  Here's one thread that may be useful.  Check Tips & Tricks forum.  I don't have enough experience to feel comfortable giving specific advice in this area . . .

[http://ubuntuforums.org/archive/index.php/t-2557.html](http://ubuntuforums.org/archive/index.php/t-2557.html)

---

### Post by snoochems on 2005-08-01
Thank for your help thus far man.  Much appreciated. :razz:

---

