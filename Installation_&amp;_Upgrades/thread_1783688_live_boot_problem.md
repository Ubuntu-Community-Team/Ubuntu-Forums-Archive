---
title: "live boot problem"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2011-06-16
I wanted to put 11.04 on my wife's Win 7 Toshiba laptop so thought I would live boot and see everything worked first.

Well it does seem to but I didn't have time to install it then so just shut down.

Well on restarting without Cd in it failed to boot windows and had to let the recovery process fix it.

Had a look to see if there was anything about this but found nothing.

Repeated the exercise and got the same problem.

Now I want to set it up for duel boot at least to start with so until I can get some answers I don't want to risk it.

Is there some problem with win 7? 

Will I be able to shrink the Win7 partition to put ubuntu on?

Will Win 7 have an error each time she boots it after 11.04 is installed and run?

Hope someone can help with any of these problems.

tia

---

### Post by linuxonbute on 2011-06-16
Anyone else got this problem?

---

### Post by oldfred on 2011-06-16
I saw your post in the old thread. But liveCD should not cause any issues as it does not use hard drive at all. 

Older versions of grub's boot loader did have some issues with windows software that wrote DRM keys into the boot area. Grub has been modified to work around flexnet, but some virus software thinks grub2's boot loader is a boot virus.

Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
 see google search on others with same issue: flexnet  site:ubuntuforums.org
Sector 32 is already in use by FlexNet

Some HP & Dell users have had issues but found that software was not essential. I have an older Toshiba and have had no issues, but do not know about newer ones.

Did you start install process? 

Once many years ago a user had an issue with windows and his network or modem card. While we all thought it impossible, it turned out that the card retained a setting from Linux and was not properly reset on reboot by windows. That version of the Linux network/modem software was later corrected to totally reset on shutdown. So anything is possible, but we have not seen many issues with liveCD.  

Do you get a windows error number?

If Ubuntu or gparted trys to open a NTFS partition that needs chkdsk or thinks it has errors, they will not open it and will set the chkdsk flag. Then windows will run chkdsk on next reboot.

---

### Post by ppv on 2011-06-16
Does Windows not start?
 
You can dual boot and there usually aren't errors. When installing Ubuntu you get an option to install it alongside Windows. But before doing so would suggest that you backup your data using live cd.

---

### Post by linuxonbute on 2011-06-16
After booting and using a 32bit live Ubuntu 11.04 windows does not start normally. Instead of that it came up with a screen which indicated that it was going to repair the O/S which it managed to do by rolling it back to a restore point.
This happened twice with a 32 bit CD which boots perfectly well in itself.
Since then I have downloaded a 64 bit Ubuntu 11.04 and ran it live and it did not cause any problem with Windows.
I have not used windows since Win 98 just slackware/mandrake-mandriva/red hat and since 8.04  just ubuntu.
So I am now downloading 11.04 32 bit to try. The one I have been having trouble with was a magazine cover disc. maybe there was something obscure wrong with it!
I will let you know how I get on.

---

### Post by linuxonbute on 2011-06-18
> **linuxonbute said:**
> After booting and using a 32bit live Ubuntu 11.04 windows does not start normally. Instead of that it came up with a screen which indicated that it was going to repair the O/S which it managed to do by rolling it back to a restore point.
This happened twice with a 32 bit CD which boots perfectly well in itself.
Since then I have downloaded a 64 bit Ubuntu 11.04 and ran it live and it did not cause any problem with Windows.
I have not used windows since Win 98 just slackware/mandrake-mandriva/red hat and since 8.04  just ubuntu.
So I am now downloading 11.04 32 bit to try. The one I have been having trouble with was a magazine cover disc. maybe there was something obscure wrong with it!
I will let you know how I get on.

Downloaded new 32 bit iso, checked it was ok with md5sum, burned a CD and checked it was ok with md5sum.
Booted it and re-booted into win7 and everything fine.
Resized win7 and installed 32 bit alongside and all works fine so I guess the cover disc was faulty in some obscure way.

---

