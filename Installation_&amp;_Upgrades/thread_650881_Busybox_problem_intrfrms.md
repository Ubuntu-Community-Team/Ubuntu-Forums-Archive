---
title: "Busybox problem intrfrms"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by Bob.Hitchen on 2007-12-26
This is a serious bug which seems to have something to do with hardware/drivers

I have 2 versions of Ubuntu 7.10; one on a AMD5200(MSI K9 Neo) with a nvidia 8500gt  works perfectly. The other  a quad core intel 6600 on a Abit IP35 Pro (Socket 775) PCI-Express DDR2 Motherboard with Nvidia 8800gt is a complete waste of space. The graphics card has its own separate issue I have the same problem if I use the 8500 card.
It won't load the live cd
It worked ok on the alternate cd until I installed updated and rebooted.
It always gets stuck looking for a disk it loaded grub off and goes into busybox Its probably due to the I/O drivers on the abit board.
Weird it will run SUSE in VESA mode (8800gt problem) on exactly the same box. Windows XP has no issues.
Has anyone solved this issue - I notice there are a few threads with variations on the same bug without resolution.

---

