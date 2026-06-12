---
title: "Ubuntu installation seems to be stuck, and no installation progress bar is visible?"
date: 2017-09-21
forum: Installation &amp; Upgrades
---

### Post by auralore on 2017-09-21
I'm installing ubuntu 17.04 for the first time, alongside Windows 10 on a new partition on my hard drive, but after beginning the installation I get to the screen showing off some of Ubuntu's features but no progress bar is visible at the bottom of the window, and it's been this way for over an hour now. Some resources I've found online state that the install should only take 15-30 mins. Is there any way for me to check what's going on with the installation, and is it possible to stop the installation safely?

Pic of where it's stuck: [https://i.imgur.com/5qNwVRO.png](https://i.imgur.com/5qNwVRO.png)

Worth noting that I'm installing from a bootable usb, and checking it for errors in grub earlier returned no errors found.

---

### Post by oldfred on 2017-09-21
What brand/model system?
What video card/chip?

UEFI or BIOS install? (how you boot install media is how it installs).

Does live installer work ok in live mode?
What does this show?
       sudo parted /dev/sda unit s print 

Are drive(s) set for AHCI? Not RAID, Intel SRT, nor IDE.
Is Windows fast start up off, if on the Linux NTFS driver cannot mount/see the NTFS partition, so then installer will hang.

See link in my signature.

---

