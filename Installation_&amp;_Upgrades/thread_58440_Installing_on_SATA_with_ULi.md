---
title: "Installing on SATA with ULi"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by TheEclypse on 2005-08-20
I have a shuttle ST20G5, which uses the M1573 Uli controller for the SATA.  When i run the installation, it tells me that it could not find any partitionable drives.  I have looked around the internet a lot for an answer to this but cant find something that works.  

Does anybody know what I should do?  I am downloading the breezy beta at the moment to see if that will work.

I have read about people installing it onto an ide drive and transfering it over - I was wondering how you go about that? surely there is something about the install that I would have to change after it has installed for this to work?

Thanks.

---

### Post by minskii on 2006-12-22
> **TheEclypse said:**
> I have a shuttle ST20G5, which uses the M1573 Uli controller for the SATA.  When i run the installation, it tells me that it could not find any partitionable drives.  I have looked around the internet a lot for an answer to this but cant find something that works.  

Does anybody know what I should do?  I am downloading the breezy beta at the moment to see if that will work.

I have read about people installing it onto an ide drive and transfering it over - I was wondering how you go about that? surely there is something about the install that I would have to change after it has installed for this to work?

Thanks.

Having the same issue too with the same Shuttle PC equipped with a SATA disk, unable to detect any partitionable drives ](*,) .  Any help would be much appreciated.

---

### Post by minskii on 2006-12-22
2 Hours later I am up and running with my Ubuntu system :) far easier an install than my Gentoo system and a lot prettier.

Anyone else that stumbles upon this thread, please be advised that there is an option in the bios of the ST20G5 to enable raid.  Doing so (even if you do not intend to use it) enables the install to progress.

---

### Post by RomanJB on 2008-03-01
> **minskii said:**
> 
Anyone else that stumbles upon this thread, please be advised that there is an option in the bios of the ST20G5 to enable raid.  Doing so (even if you do not intend to use it) enables the install to progress.

Yes! Thank you. My attempts to install 6.06 LTS on an old Shuttle XPC AMD 64 failed - blue screen after detecting the disk and "Starting patitioning..." message - until I enabled RAID!

---

