---
title: "Triple-booting"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Tangerine87 on 2007-08-31
Hey everyone, 

This is my first first post, and first time using Linux, so sorry if I ask anything stupid.

The way my computer is set up, I have my old 120gb hdd patitioned into two equal sections (the C and D drives,) with XP installed on the C, and just files sitting on the D. I also have two new drives, set up as a RAID 0 (I think that's the one,) with Vista installed on it (the G drive). Incidentally, Ubuntu can't mount the G drive, whether because it's a RAID or some other reason, I don't know.

I booted from the Ubuntu live CD, and enjoyed it, so I wanted to try it out. My intention was to install it on the D, and have a triple-boot system. But I'm nervous about installing a brand new OS, etc, so I thought I'd come here first.

Is there anything wrong with my plan? What I'd like most is the keep what currently happens, in which I'm offered a choice between booting Vista or "older windows version," with Ubuntu appearing as a third option in that menu. A lot of what I see online says that after you install Ubuntu you can just select which OS to boot to from a menu that loads up when Ubuntu does (my technical knowledge is very limited, sorry,) but what with Ubuntu not being able to mount my G drive, or figure out that Vista is installed there, I'd be worried that it wouldn't work. Which is why I want to keep the current menu for slecting an OS.

Sorry if this post is hard to understand, I tried to explain the issue as clearly as I could. I'd appreciate if you guys could tell me whether there are any flaws in my plan, and whether it will be possible to do what I would like.

Thanks in advance!

---

### Post by dabl on 2007-08-31
If can get your data files off of "D", and use that 60GB for Ubuntu, I think your plan will work fine.  I wouldn't count on Ubuntu ever seeing that RAID setup -- hopefully you don't care about that.

Your "D" partition needs to be turned into 3 partitions for Linux (OK, it only HAS to be turned into 2, but I highly recommend 3).   Use GParted, either from your Live CD, or download the ISO and make yourself a GParted Live CD just for this type of adventure, from [[COLOR="SeaGreen"]**here**[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828).

Recommended partition sizes would be:

7GB (for "/")
0.5GB (for swap)
the_rest_of_it (for "/home')

Format the / and /home partitions as ext3 (or reiserfs). You can use either GParted to do the formatting, or do that during the Ubuntu installation.

I personally like the "Alternate Install" version of the Ubuntu installer better than the Live CD - it gives a bit more visibility and control over the process.  But the Live CD will work fine.

---

### Post by Pumalite on 2007-08-31
Even if you try to install to another drive, Ubuntu will mot recognize your Raid0. Take a look at this:[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Tangerine87 on 2007-08-31
Thanks for the quick responce.

Are you saying that I need to manually turn my D partition into three seperate ones? If I have to I will, but I was under the impression that sort of thing would be done for you during the install.

Also, will it use the boot loader that I currently have come up, with just Ubuntu added as a third option? And if not, is there a way to set it up so it does?

---

### Post by dabl on 2007-08-31
> **Tangerine87 said:**
> 

Are you saying that I need to manually turn my D partition into three seperate ones? 

YES (it's not hard)

> 

Also, will it use the boot loader that I currently have come up, with just Ubuntu added as a third option? And if not, is there a way to set it up so it does?

No, Grub will be installed and will provide a boot menu, and I hope you're not thinking "sexy-looking" because it provides white text on a black screen.  (But there are ways to put a better looking background on it, later). If it were just Win XP and Ubuntu, I would say with 100% confidence that it will arrange the boot menu in a manner that will be fully satisfactory for you.  But the "Vista-on-RAID" situation is not one that I'm real confident about -- I'm not real sure what you're going to see, with that.  The problem is, if the RAID array is not recognized as a valid partition, then the Ubuntu installer will never detect the Vista OS there, and it won't be added automatically to your boot menu.  :(

So, I think that's the main risk factor in your plan. Unfortunately, I can't guarantee that there is a way to work around the failure of the boot menu to "see" the Vista OS, if the RAID array is invisible to it.  It may (or may not) be the case that your current bootloader can be modified to see the Ubuntu installation on the "partition formerly known as D".

One possibility is that you could simply say "no" at the conclusion of the Ubuntu installation when it asks if you want it to place the Grub menu.  I THINK you can do that, or else (with the Alternate Install) you can tell it to put grub in the "/" partition, where it won't actually control booting at all.  That will leave you having to patch up your current bootloader to see Ubuntu.

---

### Post by Tangerine87 on 2007-08-31
I don't care at all what the bootloader looks like, my reason for wanting the Windows Boot Loader to continue being the one I use are exactly what you said; I'm worried about not being able to get into Vista.

When I go into BIOS, I can't even set it to boot from the RAID. This may be a standard issue, I don't know. But for whatever reason in the boot priority menu, I need to set the old hdd (Maxtor) as the first priority drive, which then brings up Windows Boot Loader and lets me into Vista. My worry is that if Grub gets installed on the Maxtor, then it'll run whenever I boot from it, and therefore might make it impossible to get into Vista at all. If I'm being stupid or whatever, please tell me; I'm well aware I might be.

I'm tempted to try just saying no to Grub, but it seems like a big risk to run, if I understand the issue correctly.

My other thought was perhaps I should just wait and get another hdd. I was planning on one anyway, and a 100gb one wouldn't set me back much at all; I could just install Ubuntu on that, and then I'd know I'd be able to get into Vista by booting to the Maxtor.

---

### Post by Tangerine87 on 2007-09-01
Can anyone else think of a way around this problem? I really want to install Ubuntu, but not if it might screw up my current setup.

---

