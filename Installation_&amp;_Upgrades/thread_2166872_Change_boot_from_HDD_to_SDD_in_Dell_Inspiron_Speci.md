---
title: "Change boot from HDD to SDD in Dell Inspiron Special Edition 15R"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by jweslley on 2013-08-11
I installed Ubuntu on my laptop in HDD using dmraid as stated [here]("http://ubuntuforums.org/showthread.php?t=2036204"). But now I wanna install another Linux distro (arch) into my SSD in order to take advantage from SSD caching from newest Linux kernels (3.9+). But after the installation the system still boots into sda (HDD) instead of sdb (SDD). any help? follow my boot info: [http://paste.ubuntu.com/5974080/](http://paste.ubuntu.com/5974080/)

---

### Post by oldfred on 2013-08-11
Did you change BIOS to boot from sdb? 
But some systems will not boot the SSD as it is not seen as a bootable device, just data.

Are you using the same /home for both installs. That can lead to version issue differences and cause one system or the other not to work correctly. Best to have separate /home, but then create a shared data partition if both systems use the same UID for the user.

---

