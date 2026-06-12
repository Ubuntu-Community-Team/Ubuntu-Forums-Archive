---
title: "CAn't boot drives or Windows XP after upgrade of Ubuntu"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by wclarowe on 2010-05-24
After attempted upgrade on my dual bot drive I can no longer boot Windows XP or either of my 2 sata drive.
Please see attachment for details.  I am desperate for help.

---

### Post by dougalkerr on 2010-05-24
Mmm... I installed 10.4 at the weekend and have no problem mounting my Vista and XP partitions on my SATA drive.
I opened some photos for information without problem.
I think the only thing I had to do was give my password.
Sorry I have no suggestions.
Hope someone else can help.

---

### Post by darkod on 2010-05-24
Run the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

and if you see grub2 installed on your windows partitions, run this fix on each partition where you have windows boot files:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by wclarowe on 2010-05-24
I tried but to no avail.  Any suggestions why the installation disk won't recognize partitions on the dual boot drive even though testdisk shows NTFS and Linux partitions and the files are mountable and accessible?

---

### Post by wclarowe on 2010-05-25
Is recovered my lost partitions using testdisk.  The 2 sata drives are still not recognized at  boot and Windows won't boot from the menu but I can bot it using a rescue disk that by passes the boot menu by just clicking "Boot windows normally."
I'm considering trying to re-install Ubuntu 9.10 in place of the Ubuntu 10.04 on the dual boot drive in hope that it will again recognize all disks at boot.

---

### Post by darkod on 2010-05-25
> **wclarowe said:**
> I tried but to no avail.  Any suggestions why the installation disk won't recognize partitions on the dual boot drive even though testdisk shows NTFS and Linux partitions and the files are mountable and accessible?

There are different reasons. Can you post the results of the boot info script which should show more information?

Maybe just the upgrade went wrong and ubuntu is not functioning fully.

---

