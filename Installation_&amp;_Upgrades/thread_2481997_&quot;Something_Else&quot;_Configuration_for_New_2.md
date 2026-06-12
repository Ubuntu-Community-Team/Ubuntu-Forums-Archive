---
title: "&quot;Something Else&quot; Configuration for New 22.04 Install with Existing Home Folder"
date: 2022-12-15
forum: Installation &amp; Upgrades
---

### Post by theassociate on 2022-12-15
Currently have a corrupted version of 20.04 on one partition of an SSD drive. Wanting to do a clean install of 22.04 on a different partition of the same drive, but I want to keep my existing "Home" folder intact on my laptop's separate HDD. Have created the new SSD partition on the SSD with GParted, but I'm not sure how to configure things under "Something Else" via my Ubuntu flash drive installer. I know how to label the boot and root flags on their respective EFI and OS partitions on the SSD, but I'm not sure if setting my existing HOME folder on the HDD as the new HOME during the installation process will overwrite the data in my existing HOME folder or not. 

Am I okay simply to designate my existing HOME as the new HOME if I don't check "format"? Will this step merge the two home folders rather than replace the existing one?

Many blessings in advance for your help.

---

### Post by SeijiSensei on 2022-12-15
Yes, point your existing home partition to /home in the disk setup dialog and uncheck the format box. It will be left intact and mounted as /home on the new installation.

There's no "merging" going on. You'll be using the new installation with an entry in /etc/fstab that points the /home directory to the correct partition.

---

