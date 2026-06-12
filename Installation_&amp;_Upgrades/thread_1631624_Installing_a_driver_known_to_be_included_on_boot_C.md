---
title: "Installing a driver known to be included on boot CD"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by FrontRanger on 2010-11-26
Hi. First-time poster, long-time UNIX/Linux workstation user on the job, but relatively small amount of admin'ing skill. I have a problem whose solution I couldn't find by searching the forum archives. ([This thread]("http://ubuntuforums.org/showthread.php?t=1390979&highlight=driver+broadcom+sta") might contain the answer, but if so it was unintelligible to me.)

Long story short: I just formatted my hard drive and installed Ubuntu 10.04 (LTS) from a CD. It boots from hard disk, but I cannot get my wireless network connection to work, and I have reason to believe the problem that it requires a driver. See, if I boot from CD (same one used for the installation), then a little green icon appears. It is the same one that appears in the System -> Administration -> Hardware Drivers menu. Clicking on that icon pops up a menu with two choices for aftermarket drivers for Broadcom wireless network devices. If the second choice (STA) is selected and installed, the wireless card begins to function, and I can successfully connect.

Now when I saw the wireless networking failure when booting from hard disk, the first place I thought to look was the System -> Administration -> Hardware Drivers menu. Clearly the driver I need is found somewhere on my boot/installation CD, but I could not figure out how to install it (or even navigate to it) when booting from hard disk.

I'm sorry if this is obvious, but can someone please help me figure out how to install this driver? Thank you.

---

### Post by oldfred on 2010-11-27
welcome to the forums.

Are you connected with a wired Ethernet connection while installing. It works a whole lot better if you are. Have you enabled restricted drivers in System, Administration, Software Sources or Update Manager settings button. I check off everything on first page, so it can offer various drivers.

---

### Post by FrontRanger on 2010-11-27
> **oldfred said:**
> welcome to the forums.

Thank you!

> **oldfred said:**
>  Are you connected with a wired Ethernet connection while installing.

 It works a whole lot better if you are.

This wasn't possible for me at the moment, but...

> **oldfred said:**
> Have you enabled restricted drivers in System, Administration, Software Sources or Update Manager settings button. I check off everything on first page, so it can offer various drivers.

... this was the ticket to success. At the bottom of the first tab on System -> Administration -> Software Sources -> Settings is a box to check, by which you can enable the sourcing of drivers from CD. After I checked that box, and went back to System -> Administration -> Hardware Drivers, the same window popped up (prompting to install the Broadcom drivers) as it had when booting from CD. Ironically, it failed when I tried to activate the driver, because of a problem with the assumed name of the path to the CD. But the error message is smart and tells what file it was looking for, so I just installed each of the *.deb files as they failed. After 3 *.deb files, 4 "activate" clicks, and a restart, it now works. Yeah!

Thanks, oldfred!

---

### Post by oldfred on 2010-11-27
Glad it worked. :)

I did not exactly tell you how to do it but you managed to find it, that is very good.

You can change post to solved so others searching forum for solutions may find this. If you need instructions on [solved] they are in my signature.

---

