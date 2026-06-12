---
title: "Ubuntu 7.0.4 Install with root partition already formatted"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by RaySchroter on 2007-04-23
At Prepare disk space I have selected MANUAL
I have WIN98, WIN2K and Ubuntu-6.0.6 LTS already installed that I do not want to mess those up.

How can I reuse an old EXT3 partition (was Mandrake 10) that I want to use to install Ubuntu 7.0.4 Fiesty on?

I have tried to delete the partition and recreate it but that did not work.

I am getting the following message when I try to go Forward from Step 4 of 7.

The file system on /dev/hda8 assigned to / has not been marked for formatting. File systems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other file systems (/home, /media/*, /usr/local, etc.) may be used without reformatting.

---

### Post by rbmorse on 2007-04-23
You can just delete the existing partition where you want to install (leaving blank space) and tell the installer to put the new distro there. If it's the only blank space on the drive there is a "largest continuous empty space" option.

---

