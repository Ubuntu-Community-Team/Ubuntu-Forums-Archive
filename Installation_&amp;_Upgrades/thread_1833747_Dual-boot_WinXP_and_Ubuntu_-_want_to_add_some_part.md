---
title: "Dual-boot WinXP and Ubuntu - want to add some partitions"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by bzd454 on 2011-08-26
Hi,  kind of a noob as far as partitions etc....i have the following on my 160 GB HDD:


dev/sd1   -     NTFS  -   6 GB -   (diag)   hidden recovery partition from Samsung for WinXP
dev/sd2  -      NTFS  -  40 GB -   (boot)   Windows XP partition
dev/sd3  -      NTFS  -   30 GB  -          windows documents and portable apps, etc.
dev/sd4  -      extended  -   72 GB      
......dev/sd5   ext4     /         70 GB      ubuntu
......dev/sd6   linux-swap       2 GB


and i would like to shrink down the ubuntu on dev5 or i guess it might have to be the dev4 section(?)  and 
add in about 4 small ~10 GB windows partitions(between SD3 and Ubuntu) and leave Ubuntu with about 30 GB on the last part of the partition table(around SD10)....i have GParted on a Ubuntu LiveCD - can i do this safely without losing my WinXP and Ubuntu installs and esp my boot load sequence?  

tia for any help...

---

### Post by oldfred on 2011-08-26
Yes & no. You should be able to do what you want without loss of data, but anytime you make system changes there is a risk. Often the risk is more between the chair & keyboard. I have done the oops I did not really mean to delete **that** partition as it really has all my data. So good backups are always the recommendation before system changes.

I also do not like moving partitions right. Depending on how much data you have it can take a long time and is slightly more risky as gparted has to copy & verify all data. Shrinking from the right only has to move some data. Moving boot partition around may require a reinstall of grub. IF partition is just moved and is still the same number & UUID which it should be, then it will be ok, but best to be prepared to reinstall grub2's boot loader if necessary.

While discussing expanding shrinking is not a lot different.
Expanding an Ubuntu System Partition and related info:
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by bzd454 on 2011-09-04
thanks for the reply OldFred and apologies for my delay in responding, i had a few problems here this last week...will study the threads you have suggested...

thanks...  :)

---

