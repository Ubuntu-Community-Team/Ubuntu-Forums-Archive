---
title: "Error during upgrade SOLVED! &quot;The following packages have been kept back...&quot;"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by PopcornEaterMan on 2006-09-21
I encountered the following error when attempting to upgrade last night.  I was hoping that I could post my problem and solution and some wise soul could 
explain why this worked.  I'm hoping my pain and struggle will help someone else understand their problem as well.

Error message from upgrade attempt:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  hal hal-device-manager libhal-storage1 libhal1 pmount
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

Action to "fix"
Start to Synaptic
Go to Repositories
The "Software Sources" window pops up
Unselect NTFS-3g related sources, located at the bottom the list for me.

Start the Update Manager under System.

The installation now proceeds without errors. 

So does anyone know why removing NTFS allowed the upgrade to proceed without error?

---

### Post by Rebajas on 2006-10-07
I have a similar error whenever I do an upgrade:

The following packages have been kept back:
  gnome-cups-manager libopenal0 python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Any ideas how this can be fixed?

T.

EDIT: See [http://www.ubuntuforums.org/showthread.php?t=228788&highlight=The+following+packages+have+been+kept+back](http://www.ubuntuforums.org/showthread.php?t=228788&highlight=The+following+packages+have+been+kept+back) for solution.

---

