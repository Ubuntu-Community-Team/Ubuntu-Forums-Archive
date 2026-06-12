---
title: "How long is this supposed to take???"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by Greggle on 2007-06-03
Greetings.

So, I d/led the 7.04 iso, checked its MD5(or whatever it is??), burned the iso and then ran the 'integrity check' after I booted from the cd. All is well.

However, once I choose 'Star or Install Ubuntu' the dvd-rom just churns away. For Hours. The installation got to the point where an Ubuntu splash screen was displayed and some sweet tribal fill was played through the speakers.

After that the only other activity was a dialog telling me the GNOME display settings daemon(or whatever) could not be loaded. After I close that dialog, the dvd-rom again churns away for hours.

Finally, a desktop(as it were) appeared with two icons: Examples and Install. It looked as if a dialog was trying to display itself in the center of the screen, but it never displayed anything. The dvd drive continued to churn away.

I read that this install doesn't need to use the hard drive, but how long is this supposed to take? There were never any progress bars or otherwise indications that anything was going on other than the dvd-rom starting and stopping for extended periods of time.

When I say a long time I mean a long time. About nine hours.

I'm hopelessly lost...

-Thanks

---

### Post by wpshooter on 2007-06-03
Give us the hardware specs of your computer, especially how much memory does it have ?

---

### Post by Greggle on 2007-06-03
Right, sorry. I'm in a frenzy. It's my first time n' all.

Compaq refurb laptop
Sempron 2800
256MB RAM(224 actual. I assume the video uses it, too)
Hard disk is... 30-somethin' GB??

---

### Post by raja on 2007-06-03
> **Greggle said:**
> Greetings.

So, I d/led the 7.04 iso, checked its MD5(or whatever it is??), burned the iso and then ran the 'integrity check' after I booted from the cd. All is well.

However, once I choose 'Star or Install Ubuntu' the dvd-rom just churns away. For Hours. The installation got to the point where an Ubuntu splash screen was displayed and some sweet tribal fill was played through the speakers.

After that the only other activity was a dialog telling me the GNOME display settings daemon(or whatever) could not be loaded. After I close that dialog, the dvd-rom again churns away for hours.

Finally, a desktop(as it were) appeared with two icons: Examples and Install. It looked as if a dialog was trying to display itself in the center of the screen, but it never displayed anything. The dvd drive continued to churn away.

I read that this install doesn't need to use the hard drive, but how long is this supposed to take? There were never any progress bars or otherwise indications that anything was going on other than the dvd-rom starting and stopping for extended periods of time.

When I say a long time I mean a long time. About nine hours.

I'm hopelessly lost...

-Thanks

Looks like a problem with the ram you have. You may have to try the text-based installer.

---

### Post by wpshooter on 2007-06-03
Does the computer already have any other O/Ss installed on it ?

---

### Post by ugm6hr on 2007-06-03
You are probably better off with Xubuntu if you have 256MB shared (with video) RAM.  That should work just fine (from the LiveCD).  Otherwise, the Ubuntu alternate CD might work (but I'd stick with Xubuntu).

---

### Post by wpshooter on 2007-06-03
> **ugm6hr said:**
> You are probably better off with Xubuntu if you have 256MB shared (with video) RAM.  That should work just fine (from the LiveCD).  Otherwise, the Ubuntu alternate CD might work (but I'd stick with Xubuntu).

I sort of disagree, **IF **there is anyway I could get Ubuntu installed and to run on it, I would highly prefer it over Xubuntu !!!

---

### Post by Greggle on 2007-06-03
It has WinXP Professional SP 2. I thought you could install it(Ubuntu) alongside Windows as part of the data migration jazz.

I'm not at all opposed to a wholesale format, but I'd like to keep a Windows partition since I have to write code for Win32. University uses MS; what can you do?

But, like I said, I'll wipe the whole drive. I've backed up everything I care about.

Still, NINE HOURS!?! That's just when I gave up and booted up Windows.

And the text-based installer? How difficult is that? This is my first foray into Linux.

---

### Post by raja on 2007-06-03
The problem is not with the windows partition. Keep it if you want to. But use the text-based installer and you should be fine.

---

### Post by Greggle on 2007-06-03
I may have misinformed y'all.

There is no partition on this hard drive yet. I thought Ubuntu was going to create one for itself.

I'm currently d/ling the 'alternateCD'. That's the text-based one, correct?

Lastly, should I just format my hard drive and do a fresh install?

---

### Post by skyshock21 on 2007-06-03
Is the hard drive spinning that entire time?  Is the HDD LED lit up constantly?  If not, sounds to me like you might have a bad memory module.  Is there any way for you to swap them out and try the install again? 

If indeed the HDD is spinning constantly during this waiting process it could be you have a flaky hard drive.  It shouldn't take that long to install, and the specs on your machine aren't the cause.  You can run install Linux w/ Gnome on a system that has 128 M of RAM.  That said, you'd probably find the performance under Xfce (xubuntu) to be a bit snappier given those specs.

---

### Post by Greggle on 2007-06-03
I thought the HD wasn't needed(initially) for this install. That's what I thought it said somewhere in one of the boot options.

---

### Post by ugm6hr on 2007-06-03
If you use the AlternateCD - it will install to your HD.  Only the LiveCD doesn't require your HD to run (but obviously does to install).

PS: This suggests Feisty it needs 256MB - presumably it refers to the LiveCD?: [http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)

---

### Post by Greggle on 2007-06-03
> **ugm6hr said:**
> If you use the AlternateCD - it will install to your HD.  Only the LiveCD doesn't require your HD to run (but obviously does to install).

Hmm, it does say 256. Where did I see 128? Am I completely stupid?

If I find an install that doesn't need 256 will I need to format the hard drive or will a partition be created?

---

### Post by ugm6hr on 2007-06-03
I installed from a LiveCD - but if the options are the same, it will offer to wipe the drive for you, or create a partition (and shrink the existing Windows partition).

Although, I'm not sure how well it shrinks NTFS (modern Windows) partitions - so you may have to use the GParted LiveCD (pick the second boot option) to do that first (or PartitionMagic in Windows).

---

### Post by Greggle on 2007-06-03
Alright, I'm tryin' the alternateCD...

---

