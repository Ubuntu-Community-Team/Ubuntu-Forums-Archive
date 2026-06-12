---
title: "Need Wubi for HP machines"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by arrowcatcher on 2013-07-07
All HP computers, desktop and notebook, come with 4 primary HD partitions already present.  No place for a second OS to be installed.  On my HP desktops I simply put in a second HD, but that's not an option with notebooks.  Maybe this is a conspiracy against alternative OS's!  My Lenovo Windows 8 notebook does not come with 4 primary HD paritions, so I installed Ubuntu on that one.  But no way on the HP machines.

On my earlier Windows 7 HP notebook I simply installed Wubi and got my "dual boot" that way.  However, that's gone now, and I have two Windows 8 HP notebooks.  It's either gotta be Windows only or Ubuntu only but not both together.  I would've just got out the Wubi alternative, but that's no longer possible with Windows 8.

I don't see any obvious workaround for "dual boot" other than Wubi with HP notebooks.

---

### Post by coffeecat on 2013-07-07
Dual-booting has never been a problem with HP laptop/netbooks with four primary partitions. You simply have to delete the HP_TOOLS partition (after backing up the contents, but I never found a use for them anyway) thus removing one of the primary partitions, shrink the Windows C: partition and then create an extended partition in the free space. You can then create as many logical partitions as you need for your Linux installation.

With Windows 8, the 4 primary partition limit in mbr partition tables is an irrelevance, because I think you'll find that HP machines with Windows 8 preinstalled have GUID partition tables, which don't have that limit. [Dual-booting with UEFI machines with GUID partition tables]("https://help.ubuntu.com/community/UEFI") adds its own measure of complexity, but you don't need wubi.

---

### Post by arrowcatcher on 2013-07-07
Thanks very much for this information.  I wasn't sure about deleting one of those partitions.  HP could've put the tools in the OS partition in the first place!

I've always dual booted Windows and Linux, but the two Windows 8 machine scenarios I've done previously have been very messy head scratchers.  So unfortunately I'll probably put this off. But it was important to know that the space is actually available.

---

