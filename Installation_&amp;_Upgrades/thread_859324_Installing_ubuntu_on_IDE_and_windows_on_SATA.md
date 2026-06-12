---
title: "Installing ubuntu on IDE and windows on SATA"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by thef0rce on 2008-07-14
Hi,

I've been thinking about installing Ubuntu on an IDE drive. The motherboard I am using has both IDE and SATA. I have windows installed on a SATA drive. I was wondering how I could install Ubuntu on an IDE drive and still be able to boot either windows or Ubuntu using grub without having to switch boot devices in the bios. Would grub be able to install itself to the SATA drive or am I just better off switching boot devices in the bios?

Many thanks in advance

---

### Post by louieb on 2008-07-14
Sure it can be done. The one problem you may encounter is the GRUB installer makes a guess as to which drive is 1st in boot order and installs a pointer to the grub program in that drives MBR. 
Sometimes it guesses wrong. (seems that this is a problem only if the PC has a mix of ide and sata drives). 

The machine boots straight to windows you never see the grub menu.
You can use BIOS to switch boot order or you can alter the MBR of the 1st drive to load GRUB instead of window. May want to look at this thread before you begin. [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902") 

Then again It may guess right and your up and running without the extra setup step.

---

