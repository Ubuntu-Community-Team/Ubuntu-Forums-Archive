---
title: "Reinstalling Ubuntu with existing /home partition"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by MikeBenza on 2007-06-10
I have a dual boot system with the following partitions:

/dev/sda1/: NTFS Windows partition
/dev/sda2/: ext3 Ubuntu partition (/)
/dev/sda3/: ext3 home directory (/home)
/dev/sda4: swap

I access sda3 from Windows using fs-driver.  The Ubuntu installation is completely hosed.  I'm not even sure how it happened, but one day it just wouldn't boot up and gave about a million errors.  In any case, I'm ready to reinstall Ubuntu.  I've a 7.04 CD.  I'm ready to reinstall.

I booted the 7.04 CD and started installing, manually configured the partitions, and the installer searched for an installation to import account settings (or was it just the accounts themselves?) from.  It found my Windows installation, but didn't find any accounts to copy settings from (or just accounts to copy?  I don't remember).  In any case, I have /home/mike as my home directory on /dev/sda3.  I want to have the same username on the new installation.  **Will the installer erase my current home directory  and replace it with a new user's home directory?**  (And yes, I have it all backed up, locally and off-site)

- Mike Benza

---

### Post by MikeBenza on 2007-06-10
*bump*

This seems like a pretty simple question...

---

### Post by ABCC on 2007-06-10
Short answer: Nope

As a distro itnerant I do this quite regularly. It's fairly straightforward to swap /home between different installs. However, there are a few caveats. If, say, certain programs that you have manually added to your menus arent installed on the new/other system then those menu items wont work. Missing themes occasionally cause headaches too, if youre using one of the default one this isnt a problem.  If X fails to load it's best to rename your ~/.gnome and ~/.gnome2 and ~/.gconf folders and try again, as these tend to be the culprits.

Generally though reinstalling this way isn't a problem and it sure saves a lot of hassle reconfiguring.

---

