---
title: "Install from USB key to HDD with base install from USB key rather than the Internet"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by aaronjb on 2010-11-22
Hi Guys,

I've been googling this and searching here now for some time, and something that seems as though it should be so simple seems .. so difficult :)

I've built a USB key install using UNetbootin and the ubuntu 10.04.1 LTS server CD image; it boots fine and can be used to install the system without problem.

However, for speed and ease of use I'd like to have it pull the base packages from the USB key rather than from an Ubuntu mirror - just like the CD installer appears to have the option of doing.

Is that possible? The closest I got to instructions for this just said 'extract the ISO into a directory of the same name on the USB key,' but that doesn't seem to be cutting it for me.. and everything else I find is about installing Ubuntu *to* a USB key, which isn't what I want to do ;)

Any suggestions appreciated :)

Thanks!
Aaron

---

### Post by arubislander on 2010-11-22
Are you saying that your system won't install from USB without an internet connection?

---

### Post by aaronjb on 2010-11-22
> **arubislander said:**
> Are you saying that your system won't install from USB without an internet connection?

Precisely it yeah :) Unlike the CD based install, when the installer is running from the USB key it forces me to download all the base installation files from an Ubuntu mirror.

---

### Post by ajgreeny on 2010-11-22
No it doesn't!

Or at least , it shouldn't do so.

Ubuntu 10.10 asks you if you want to download updates and some codecs at the same time as you install, but that option was not in 10.04, not the desktop version at any rate, and I don't think the server version should be any different.

What actually happens if you try to install with no internet connection?

---

### Post by aaronjb on 2010-11-22
Well.. it does for me :)

If I try to install with no internet and bypass the DHCP configuration option it'll simply tell me that it was unable to contact any mirror, and go no further (that's the step immediately after configuring the network)..

[edit] That is using the USB key I created (which, using the utility, has an identical file structure to the CD with the addition of the syslinux directory) - using the CD Rom I can continue without network connectivity and the base packages are pulled from the CD.

---

### Post by ajgreeny on 2010-11-22
Well, apologies if I got it wrong, but that is a very strange situation and I certainly did not know that the USB is different from the CD.

---

### Post by aaronjb on 2010-11-22
No worries :) I thought it was meant to operate the same regardless of the installation medium, but .. it doesn't seem to :(

I think normally (not at work now, so I can't check) a CD install would mount the installation media under /media, no? But the installer doesn't mount the USB stick anywhere, so you just have the contents of the initrd and thus no /pool directory once the installer is running.

I figure I'm either missing something silly (like I created the USB key wrong) or it's not meant to work that way :)


Oh and this could be specific to the Server CD - I haven't actually tried a Desktop CD image yet (frustration set in ;) )

---

### Post by aaronjb on 2010-11-23
So after more headscratching and general confoundery today, a colleague and I got it working..

Well, ok, he did.

He installed Ubuntu Desktop in a VM and used that to create the bootable USB stick of Ubuntu Server - boot from that and everything works fine and as described above, all the files are pulled off the USB key rather than forcing you to use the internet for the initial load.

So it seems the problem is actually somewhere in UNetbootin/Universal-USB-Installer-1.8.1.2 on Windows rather than anything specific to Ubuntu.

Anyway.. problem solved ;)

---

