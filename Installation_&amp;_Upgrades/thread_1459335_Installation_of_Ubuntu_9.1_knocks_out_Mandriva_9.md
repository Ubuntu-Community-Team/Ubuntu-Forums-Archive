---
title: "Installation of Ubuntu 9.1 knocks out Mandriva 9"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by dalpets on 2010-04-21
Hello,
Up until yesterday I had a working Mandriva 9 installation but after installation of Ubuntu 9.1 grub cannot find the Mandriva installation (the info for Mandriva still exists in Grub).

The partitons that existed before installing Ubuntu were as follows;
/dev/sda1 ntfs (free)
/dev/sda5 ext3 (Mandriva)
/dev/sda6 swap

For Ubuntu I added the following logical partitions;
/dev/sda7 ext3
/dev/sda8 swap

Should I have used /boot instead of / for each of the installations?

Also,should I have used two swap partitions for the two installations ,as I did,or did I only need the original Mandriva swap for both installations? I ask this because when I was finalizing the Ubuntu partitions sda6 appeared not sda8.

Any help for a relative newcomer to Linux, would be appreciated.

---

