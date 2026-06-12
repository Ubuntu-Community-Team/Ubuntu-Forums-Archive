---
title: "Can not create boot USB in order to upgrade"
date: 2022-11-24
forum: Installation &amp; Upgrades
---

### Post by hotasianteeen on 2022-11-24
Hi all, 

Sorry I am an UBUNTU newbie, and I have tried to make this work. But can not seem to get it done.  

I have an AMD 2 TB HD and 1 TB RAM machine that enters into Bios fine.  It was running 18.04.  For some reason it did not want to update.  I ended up attempting a clean install. 

I have BalenaEtcher Version 1.7.9 (1.7.9), and I created a USB device from ISO.   I do this from a Mac book pro.  I am trying to install  ubuntu-22.10.1-desktop-amd64 
I can load from this and get the install or try menu.  The try menu freezes right away.  The Install menu allows me to get to the screen "Almost finished, just copying some files ... and hangs. 

I have tried:
- using Rufus etcher from a windows machine (same result)
- installing 22.04 (same result)
- using minimal installation (instead of normal)
- allow 3rd party updates and not (same result)
- using ZFS format 
- allowing downloads during load, 
- not allowing them, 
- installing a previous version 21.10
- loading system rescue-9.05-amd64 (WORKS!) and erasing drive and reformating it as ext4 for both drives; removing partitions; formating the usb in FAT format
- installing on the RAM
- loading with secure disk ON 
- Loading with secure disk off (Bios)
- disabling Quik boot and enabling it.  


I have searched almost every forum.  I cant find what its missing or how to go on.  Please if someone could guide me in the right direction, I would be very happy. 

-THanks in advance.

---

### Post by C.S.Cameron on 2022-11-25
If you have UEFI you can just extract the ISO to an NTFS partition. It should show up in the UEFI menu as UEFI USB or similar.

---

### Post by hotasianteeen on 2022-11-25
Hi thank you for your response. 
It does appear in the UEFI as USB, 
it goes to the instalation menu (Try or install)
I proceed through the settings and it fails during the loading files.

---

### Post by guiverc on 2022-11-25
> **hotasianteeen said:**
> 
I have BalenaEtcher Version 1.7.9 (1.7.9), and I created a USB device from ISO.   I do this from a Mac book pro.  I am trying to install  ubuntu-22.10.1-desktop-amd64 


I'd suggest checking what you actually have, as your details don't look correct to me.

For Ubuntu 22.10 DESKTOP I'd expect to be 

[https://releases.ubuntu.com/kinetic/ubuntu-22.10-desktop-amd64.iso](https://releases.ubuntu.com/kinetic/ubuntu-22.10-desktop-amd64.iso)

ie. 22.10 and not 22.10.1 you mention in your original question; thus your issue maybe an invalid/corrupted/illegitimate ISO. 

Ubuntu 22.10 is not a LTS release, thus has no point (*replacement*) ISOs created; though there have been exceptions (eg. 17.10.1 existed!) but that's only when a flaw is detected with the installer/ISO causing a re-creation of the ISO.  There are *point releases* for LTS releases (so 22.04.1 exists).

I'd suggest skipping the *minimal* install if you can (*it does a full install, then after that creates the minimal install by removing files from the install* *using a droplist*).  I'd also switch to a text terminal when it *'hangs**'* and look for clues on why, both in looking at logs (*maybe reoccurring errors/warnings in `dmesg`, or `journalctl`, I also look out for squashfs errors as that is how read errors in your input media usually show; ie. if your ISO was corrupted to you had a bad write to install media*).  What you does vary on release & ISO, but it's easier for desktop ISOs (*using `ubiquity` especially*).

---

### Post by ian-weisser on 2022-11-25
> **hotasianteeen said:**
> 
The try menu freezes right away.  The Install menu allows me to get to the screen "Almost finished, just copying some files ... and hangs. 


This strongly suggests that your install media is corrupt or incomplete.

Re-download.
Look up how to check the hash to confirm a good download.
Then re-create your LiveUSB.

---

