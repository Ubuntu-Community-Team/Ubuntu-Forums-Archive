---
title: "distro upgrade, forgot to export virtualbox virtual machine, ooops"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by sippyCUP on 2010-08-29
Hey all,

I recently upgraded from Ubuntu 8.04 to 10.04 and have a bit of a pickle... I ran winxp virtualized via virtualbox OSE and I stupidly assumed that I would just need the .vmi file of my windows xp guest and I could import that into virtualbox OSE after I installed it from repositories onto the new OS. :confused:

So unfortunately I entirely neglected to export the virtual machine. The silver lining is that I still have a full backup of my previous 8.04 install, so I have access to the virtual machine file (i think it's in xml actually) and save states.

Does anyone know if there is any way of getting my virtual machine set up properly on my new install short of restoring ubuntu 8.04 from my backup, exporting, then reinstalling my 10.04 image and importing into virtualbox OSE? I found info for exporting this stuff but not for my current situation.

EDIT: should mention I tried just transfering the VDI and creating a new virtual machine, but something on the hardware level must have been different from the VM I used to install winXP, because windows errored out on boot.

Thanks for your time,
Eric

---

### Post by sippyCUP on 2010-08-31
Okay guys, this was actually a really easy fix.

Since I created the WinXP virtual machine (many Virtualbox versions ago), the default setting for the IDE controller has migrated from PXII3 to PXII4.

When I tried to boot from a PXII4 VM an install of WinXP that had been done on PXII3 "hardware," it balked.

The solution was to switch the VM IDE controller setting back to PXII3.

---

