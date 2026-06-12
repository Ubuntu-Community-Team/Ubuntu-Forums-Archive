---
title: "Can I Update from 11.4 In Situ?"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by nudnikian on 2012-10-06
Project dump Win8.  New asembled box - Gigabyte GA75M AMD A4 

For unknown reason my Ubuntu 12.4 pendrive stick would not install, so I found v11.4 cd which worked and is running very nicely with beautiful screen res, etc. 

I am having a devil of a time finding v11.10, but before I do that - 

I understand I must update in two stages, 1st 11.10, then 12.4

Is it possible to download these two install pkgs to folders on my current 11.4 , and update from a live system?  Or must I load them from ext drive?   How about an Ubuntu server?

OK I'm clueless but I've een searching on FF and sys guide for an hour.  Point me to an update page or whatever.   I want to get latest OS LTS installed and all major security updates etc . Make certain all is compatible before engaging in application installs, customizing and configuration.  Thanks

---

### Post by patriot56 on 2012-10-07
> **nudnikian said:**
> Project dump Win8.  New asembled box - Gigabyte GA75M AMD A4 

For unknown reason my Ubuntu 12.4 pendrive stick would not install, so I found v11.4 cd which worked and is running very nicely with beautiful screen res, etc. 

I am having a devil of a time finding v11.10, but before I do that - 

I understand I must update in two stages, 1st 11.10, then 12.4

Is it possible to download these two install pkgs to folders on my current 11.4 , and update from a live system?  Or must I load them from ext drive?   How about an Ubuntu server?

OK I'm clueless but I've een searching on FF and sys guide for an hour.  Point me to an update page or whatever.   I want to get latest OS LTS installed and all major security updates etc . Make certain all is compatible before engaging in application installs, customizing and configuration.  Thanks

Greetings nudnikian.
Just to be clear, I am in no way qualified to answer all of the questions you ask, being new to Linux myself.  That said, you mentioned in your post that you were under the impression that you need to "update in two stages, 1st 11.10, then 12.4".

Have you considered just doing a clean install of 12.04 from a Live CD/DVD? 
Assuming that you have the ability to download an .iso file and burn it to CD/DVD you can obtain the latest stable release from [here]("http://distrowatch.com/").
Once you have downloaded the distro. that you want it is a simple task to burn that file to a "bootable" disk therefore creating a Live CD/DVD.

There are many great applications out there that you can download to burn the downloaded .iso to disk.  My favourite for this task is K3b.
Just remember, it is recommended that you burn at the lowest possible speed.

I hope this helps.
Oh, and welcome to the Forum

---

### Post by coffeecat on 2012-10-07
> **nudnikian said:**
> 
For unknown reason my Ubuntu 12.4 pendrive stick would not install, so I found v11.4 cd which worked and is running very nicely with beautiful screen res, etc. 

With a fairly recent board such as that, and since 11.04 works OK, there shouldn't be any reason why you can't install 12.04 directly. Much better than installing 11.04 and doing two version upgrades. You need to see if your 12.04 installation medium is OK.

Also - I've been trying out a Gigabyte board which has the same hybrid UEFI BIOS as yours (I believe) and I found the EFI implementation troublesome. The 12.04 installation CD can boot in EFI mode, but not 11.04 iirc. Although you were using a pendrive, and I couldn't find a way of getting this to boot in EFI mode with the Gigabyte board, this may be a factor. What BIOS settings do you have?

---

### Post by nudnikian on 2012-10-07
I'll keep searching, thanks.  

 I got the system to update.  You MUST update from 11.04 to 11.1 - cannot jump to 12.04. You have to refresh the Update Mgr first so it knows the next Update pkg.  It installed 11.1 and then promptly died.  Methinks lacking something in the drivers pkgs necessary for FM1 socket boards. I posted in absolute beginners and got lead to 12.04 alt-iso which may work, Thanks

---

