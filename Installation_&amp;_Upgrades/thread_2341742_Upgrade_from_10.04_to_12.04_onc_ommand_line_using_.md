---
title: "Upgrade from 10.04 to 12.04 onc ommand line using ISO, no internet access"
date: 2016-10-31
forum: Installation &amp; Upgrades
---

### Post by clipper74 on 2016-10-31
Hi Folks,

I have a thin client machine with local storage and an Ubuntu 10.04 LTS installation. I need to upgrade this to 12.04. I cannot do a clean install due to the application on the box, I don't have the installation media for it and the client won't give me it so this must be an upgrade.

Being a thin client, the box does not have a CD/DVD but it does have a USB slot. I have a 12.04 TLS ISO image on a USB stick and I can mount the image as a filesystem.

Most of the upgrade instructions tell me to simply run update-manager and click this and that. I however do not have a GUI, this is all command line stuff.

I'm looking for instructions therefore on how to upgrade form 10.04 to 12.04 using the mounted ISO image on a non-internet connected box using just the command line. Sounds simple but I can't find anything online to help me.

Foobsy

---

### Post by TheFu on 2016-10-31
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
10.04 Desktop EoL was in 2013.
12.04 Desktop EoL is in a few months.
Best to get onto a newer release, though it might require going through 12.04 to get there.

Regardless, I believe forum policies limit the help allowed for unsupported releases, but doubt I could help anyway with the info provided.

---

### Post by Bucky Ball on 2016-10-31
[Here's an option]("https://help.ubuntu.com/community/EOLUpgrades"). As mentioned, we don't officially support EOL releases here. One reason is because many people have forgotten about them and moved on and can't give a lot of support anyhow. Another is that they are no longer supported by Canonical.

My advice would be to back up what you don't want to lose and install 16.04 LTS directly. You will then be supported until 2021 and you can upgrade directly to 18.04 LTS sometime after 2018 (and any time before 16.04 LTS reaches EOL) which will also (at this point) have five years support, being an LTS release.

Even if you could get to 12.04 LTS, as also mentioned previously, you would then need to get to 14.04 LTS quick smart as 12.04 is only supported for another six months or so. Upgrades take a few hours and are often problematic. I avoid them personally and install the next LTS on another partition when it comes out and play around with it until it is stable and I'm confident enough to move operations from the old LTS to the new. 

Good luck. :)

---

### Post by clipper74 on 2016-10-31
I suppose I should have said the ultimate goal is to get to 16.04 and 12.04 is the first step in this process. We won't be stopping at 12.04 because, as you have said, it goes out of support soon.

I had hoped that it was an easy process and I could update to 12, then 14, then 16. The direct update to 16 is not possible because of the application. We don't know anything about it and have no way of knowing if the whole app is getting backed up and if a restore would work because it is a thin client. i.e. it gets info from a backend we have no control over.

Thanks

---

### Post by ian-weisser on 2016-10-31
The upgrade path from 10.04 to 12.04 to 14.04 to 16.04 may or may not work.
The big unknown is the non-Ubuntu software. Best practice is to uninstall non-Ubuntu software before upgrading. If that software relies upon obsolete standards or subsystems (sysvinit, HAL), then it might simply be incompatible with a modern release of Ubuntu.
Lesser unknowns include Ubuntu software that may have changed or been abandoned since 10.04.
A pristine, stock 10.04 system will smoothly upgrade...that upgrade path is carefully tested. But there's way to know how close to that state your thin client is.

Can you clone the thin client into, say, a VM and try the upgrade from there?
I think you need some kind of copy to experiment upon. Too many unknowns.

---

### Post by clipper74 on 2016-10-31
Thanks ian-weisser. The This client I have is for testing only. It will be wiped and re-imaged once I've tested upgrades etc. It is my experimentation box. If the software fails after the upgrade stages then we will need to re-evaluate the project but I can't even get off the ground on updating Ubuntu.

You said the upgrade path is carefully tested but I can't find a method online that shows the step by step instructions on how to do it when all I have is an ISO image and a CLI. That being the first step is the one I'm trying to find.

Foobsy

---

### Post by TheFu on 2016-10-31
[https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/) and [https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html) doesn't work?

I would expect the old software to break, especially if it is a GUI app. The GUI libraries have drastically changed in the last 6 yrs.  CLI software probably will continue to work, unless it is tightly integrated with specific HW or old-stype networking.  But you never know until it is tried - well - trying is the easiest way. Static analysis of the system and library calls used could predict issues, but that is non-trivial.

---

### Post by ian-weisser on 2016-10-31
> **clipper74 said:**
> You said the upgrade path is carefully tested but I can't find a method online that shows the step by step instructions on how to do it when all I have is an ISO image and a CLI.

The normal desktop/server install images are not intended to be used for upgrading. Use the alternate image for upgrading.

For a method that works very well,see [http://askubuntu.com/questions/39105/how-to-upgrade-ubuntu-from-an-iso-image](http://askubuntu.com/questions/39105/how-to-upgrade-ubuntu-from-an-iso-image)

---

