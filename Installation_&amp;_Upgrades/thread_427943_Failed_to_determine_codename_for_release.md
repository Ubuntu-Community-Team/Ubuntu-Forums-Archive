---
title: "Failed to determine codename for release"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by oneeyedelf1 on 2007-04-29
I am installing ubuntu via this method [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) (due to a broken cdrom) and I am using the alternate cd (due to issues with the livecd)
so my install goes along and then halts durin the detection of my cdrom, so I fix it by mounting /dev/hda5 to /cdrom and start continuing along my way untill I get to install base, where it says "Failed to determine the codename for the release" and now I am stuck. I have read from otherplaces that the manual mount is causing this error, but I don't know how to fix it.

---

### Post by ljp37 on 2007-06-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/122402](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/122402) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I think I've found a workaround for this.  After you mount another partition or an ISO to /cdrom, get to the installer menu and choose "load installer components from cd".  Install the machinery for detecting and loading ISOs.  Then unmount your /cdrom (and whatever other partition you may have mounted) and let the installer detect and mount the ISO.  The release codename will be correctly determined and you will be able to install the base system.

---

### Post by cjwatson on 2007-07-04
This type of installation is not generally supportable: you will find that many partitioning scenarios unavoidably fail later if you do that, since the kernel will have the partition table locked and will refuse to re-read it without a reboot. I'd recommend using the documented method to install from USB instead if at all possible.

---

### Post by ScribbleJ on 2007-12-17
I just had this same problem installing Ubuntu Server 7.10 /from cd/ to an old PIII-750.

Everything else seemed to work fine and I wasn't doing anything unusual.

I worked around it by returning to "load installer components from cd" and chose the component that lets you choose network mirrors, and installed from the network instead of from the CD.

Hope that helps someone.

---

