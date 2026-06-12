---
title: "XFS no-can-do??"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Seti on 2007-04-20
Just tried to install Feisty Fawn. The installer complains about / being on /dev/sda6, which is formatted as xfs. Installer complains that it cannot use grub because an error will ensue
a little window pops up saying:
```

The GRUB boot loader installation often fails or hangs when /boot is on a XFS file system. Using LILO in this situation is recommended.

```
and NO option to use lilo instead of grub is offered! The two options are go back, or continue anyway!
?????
Is it me or is Ubuntu's installer getting worse with each release?

---

### Post by Seti on 2007-04-21
nobody?!?!

---

### Post by Seti on 2007-04-22
hard to believe that body else has had this same error or knows what I'm talking about. 
Sorry if my first post in this thread sounds negative. Thing is, I really like ubuntu and the debian way of doing things, but I've been finding that Edgy and now Feisty are very problematic in installing. For Edgy, I had to get a CLI OEM-install disc; couldn't use the liveCD.

Any ideas?????

plz help

---

### Post by jdong on 2007-04-22
That is a legitimate warning that has been in every Debian and Ubuntu release and appropriately applicable.

Due to an interaction between GRUB and XFS, sometimes the grub-install command will hang when the installer attempts to install grub to an XFS partition.

Unless you are comfortable with installing grub by hand in case the installer hangs, you should make a separate ext3 /boot partition (roughly 100MB in size) so that GRUB can reliably install.

---

### Post by Seti on 2007-04-24
I downloaded the alternate-install iso for Feisty and used it to install; it had no problems installing lilo as required. 
I had a similar problem before with Edgy; using the alternate-installer saved the day. It seems that the graphical liveCD/installer has issues with various partition-schemes, and in browsing through these forums I see that I'm far from alone. 
Anyway, problem solved. Thanks!

---

### Post by mody on 2007-04-30
I was hit by this last evening. I know about problems with GRUB and XFS. But for me
```
xfs_freeze -u /
``` always helped. The other way is to install LILO and then replace it with GRUB. 

With such knowledge I choose XFS as my root FS during Fiesty installation. I got two warning messages which I've expected. Both offered two buttons "Go Back" and "Continue". During the partitioning the first button means "Go Back to installer" ie continue and the other button means "Continue partitioning". The second warning had different means of buttons. :-( "Go Back" meant stop the installer and "Continue" meant continue the installation but with GRUP and not with the suggested LILO, which of course failed. I had to install grub by hand, use the unfreeze trick to get bootable system. The installer disapointed me... :-(

Mody

---

