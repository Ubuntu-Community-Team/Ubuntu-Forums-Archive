---
title: "Keeping an installation &quot;generic&quot;"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by Xarthos on 2011-01-14
For about a year now I've been running an Ubuntu Live USB peristent image on my USB flash drive for portable computing. I tend to switch computers on a near-weekly basis because of my job, and I really like having a consistent desktop to work with. Plug in the USB, boot the machine, and go. The only drawback has been that the LiveUSB installation isn't really designed for daily usage, and I've run into problems with the FS and horrendous boot times on some machines.
 
A few days ago I stumbled across a site that described something I'd been thinking about for a while...simply performing a normal installation onto my 32GB flash drive. As it turned out, the installation was painless...until I tried to switch computers.
 
I quickly discovered that the Ubuntu 10.10 installation would boot fine on the original hardware that I performed the installation on (a Dell Precision Workstation), and on other similar workstations, but it will NOT boot on my home computer (a Dell XPS), on my HP or Asus laptops, on my friends Gateway, or on the low-end Inspirons in our student labs. I even tried wiping it and replaced Ubuntu with Xubuntu, hoping that the lighter install would be more flexible. No dice. Same result. Stops responding at random places during the boot sequence, but most frequently when trying to initialize the HDD controller.
 
I think I've identified the problem though...drivers. Ubuntu, like most operating systems, appears to do basic hardware detection and installs the drivers needed to run on the host computer during installation (please correct me if I'm wrong on this). When the drive is swapped into another computer with radically different hardware, it can't boot because it's trying to initialize the wrong drivers.
 
Which begs the obvious question...is it even possible to perform a "generic" Ubuntu installation that will work the same way the LiveCD does, detecting hardware on bootup and running on* any* hardware? I really don't want to go back to the LiveUSB version, but having a portable Ubuntu installation does me no good if it only runs on one type of computer.
 
Has anyone got this to work?

---

