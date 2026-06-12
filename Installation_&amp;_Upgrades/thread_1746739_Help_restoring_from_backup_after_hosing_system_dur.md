---
title: "Help restoring from backup after hosing system during 11.04 upgrade"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by tnine on 2011-05-02
Hi all,
  I have a workstation that was an Ubuntu server 10.10 with the ubuntu-dekstop package installed.  I recently tried the online update, only have my system fail to boot.  Unfortunately after an entire day I've been unable to get grub to mount my raid 5 array, then the LVM within it during boot.  I've thrown in the towl, and I've purchased another drive and now have LVM running over 2 pairs of Raid 1 disks.  I'm all sweet and I have the desktop environment set and running with a bare 11.04 installation.

I have a backup that is a back in time backup.  It is the full system except for the /media and /tmp directories.  I initially thought I could just rsync it, however the backup is from version 10.10.  Any ideas how I can migrate this to a 11.04 distribution then rsync it to restore all my configurations and user settings?

Thanks,
Todd

---

