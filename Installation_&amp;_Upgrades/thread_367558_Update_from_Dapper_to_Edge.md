---
title: "Update from Dapper to Edge"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by reb68 on 2007-02-22
I have been trying to update from Dapper to Edge because I am told I need to be in Edge when Fiesty is released. I am booting for the .iso I burned and when I get to install I follow to when it asks about formating partitions. I format the swap as I want to preserve my Documents and Files. I then get the error that I have NO root file.
Following is what I have and how can I correct it.
----------------------
Partition 1--38.7 Gb   /home   ext3    /dev/hda1  Enabled
Partition 2   1.4  Gb   none     swap  /dev/hda2   Enabled
Partition 3  34.5 Gb   /           ext2   /dev/hda3   Enabled
-----------------
I also have another drive with WindowsP Pro on
Do I need to create a root with "Gpart"

---

### Post by taurus on 2007-02-22
If you want to upgrade from Dapper to Edgy, use this guide.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Kateikyoushi on 2007-02-22
I think you only need to set the mount point as / for hda3.

---

### Post by reb68 on 2007-02-22
I ha tried doing the "update manager" as suggested in the kubuntu install page. When I click on update (when it shows me that an update is availabe at the top) it runs to files down in the center and then gives an error that DCOPserver is not installed. Should this be in the 6.06 that I already have?
I dddi have the Partition 3 as "/"

---

### Post by Kateikyoushi on 2007-02-22
I mean when you install, and if you choose the complete reinstall set the mount points for the drives as they are now but only format the / partition.

You could try to install dcopserver it might continue with the upgrade but I can not see why is it crucial.

---

