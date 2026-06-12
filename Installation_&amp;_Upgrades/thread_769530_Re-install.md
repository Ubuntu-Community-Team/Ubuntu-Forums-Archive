---
title: "Re-install"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by skywalker2208 on 2008-04-26
I was wondering of how to reinstall ubuntu.  I recently was upgrading to the newest version of ubuntu and the upgrade seemed to go fine until I restarted the computer when the prompt asked to restart the computer.  I try to load into the new version and it doesn't seem to work.  I know want to just reinstall it and not sure of how to go about it.  I load in the cd and go to the manual partition option and then I am lost.  I looked around here and through google and don't find any step by step guide.  Any help would be appreciated.

---

### Post by Tatty on 2008-04-26
Do you have any partitions you want to save (eg, a windows partition) on your hard disk?  If not just choose erase entire disk.

If you dont want to erase everything then the easiest way to re-install ubuntu is to load gparted from the liveCD (System->Administration->Gnome partition manager) and manually delete your ubuntu partitions (which should by default consist of an Ext3 partition and a swap partition).  Then start the installer choose the option "use free space" (or something along those lines)

---

### Post by skywalker2208 on 2008-04-26
thanks that seemed to have worked.

---

