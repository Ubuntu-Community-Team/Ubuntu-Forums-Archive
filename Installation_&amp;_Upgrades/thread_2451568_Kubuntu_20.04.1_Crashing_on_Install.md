---
title: "Kubuntu 20.04.1 Crashing on Install"
date: 2020-10-06
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2020-10-06
I spent about 6 straight hours last night trying to get Kubuntu 20.04.1 installed.  The installer kept crashing.

At first, it crashed on the installer where you enter your username / password and Computer ID.  It would tell me the CD/DVD is corrupted, or the USB is corrupted, etc.
So, booted Windows, ran Rufus, and did a really slow installation to the USB that verified the install.

At the next attempt to install, it would get past the username / password part, and start the actual installation.  Then when the bar hit about 90%, it would crash stating that an unknown error had occurred, and the installation would be halted.

I booted back into Windows and installed 20.04, figuring I could install this, and then upgrade after installation.  Same problem as before.
Tried a different USB drive.
Tried downloading another ISO and ran the checksum...  Tried it on even another USB drive...

Same thing keeps happening over and over.  Finally, at around 1am, I decided to give up and go to bed.

I have never had an issue with installation before.  I even had 20.04.1 installed before with no issues.  What could the problem be?

---

### Post by Shibblet on 2020-10-07
Ugh...  [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1871268]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1871268")

---

### Post by ActionParsnip on 2020-10-07
Did you MD5 test the ISO you downloaded?

---

### Post by Shibblet on 2020-10-07
> **ActionParsnip said:**
> Did you MD5 test the ISO you downloaded?

Yes.  On both 20.04 and 20.04.1

---

### Post by ActionParsnip on 2020-10-07
Have you tested your RAM health to make sure that is OK? This installer runs entirely in RAM so bad RAM will cause issues

---

### Post by Shibblet on 2020-10-07
> **ActionParsnip said:**
> Have you tested your RAM health to make sure that is OK? This installer runs entirely in RAM so bad RAM will cause issues

Yeah, it's not the RAM, but thank you for the suggestion.  

Apparently it's an issue with the Nvidia Drivers that are pulled down during install if you check "3rd Party Drivers" when installing.  At least that is what the bug-tracker is saying.  When I get home tonight, I'll give installation another try and not check that box and/or disconnect the Ethernet on install.  I can update once I get the OS installed.

---

### Post by Shibblet on 2020-10-08
Alright!  That worked

What I had to do:

Boot from USB into Desktop Mode
Disconnect the Internet
Start the installer
UNCHECK Install 3rd Party Drivers
Install as usual.

After the installation, do a software update.  (Theres a lot more than normal)
Install Nvidia Drivers in "Software Sources"

All is well.

---

