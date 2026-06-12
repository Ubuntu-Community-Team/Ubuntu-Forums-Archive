---
title: "Can't install Kubuntu with GA-P31-DS3L abd 8500GT"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by bluman on 2008-03-22
Hi all,

I have tried for days now to install Kubuntu 7.10 using the following hardware:

Intel 2.6GHz Core 2 DUO processor
Gigabyte GA-P31-DS3L motherboard
2GB RAM
Gigabyte PCI-E 8500GT Video Card
320GB SATA Hard Drive
SATA DVD/RW

When booting from the Live CD (i386 version) the boot process fails when kdm attempts to load. I have followed various threads trying to disable ACPI etc...

Has anyone got this working and if so, what magic step do I need to make it happen?

Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-03-22
Use the Alternate CD to install. You might need to configure your xserver at the end of the installation.

---

### Post by bluman on 2008-03-22
Thanks Pumalite, I'm downloading the alternate CD now and will report back here after attempting the install.

---

### Post by bluman on 2008-03-24
The alternate install CD worked however for some reason the Gigabyte 8500GT (512Mb) changed to the DVI output when starting X so using the included DVI to VGA adapter, I plugged my monitor into the DVI output and it worked! Weird!

Once KDE had loaded I was then prompted to install the restricted drivers. I did this by going into System -> clicking on the advanced tab -> clicked the "Administrator Mode" button and entered the password then ticked the box next to the nVidia drivers. KDE downloaded and installed the drivers correctly. Once I rebooted, the restricted drivers worked fine.

Now onto my LinuxMCE install!

---

