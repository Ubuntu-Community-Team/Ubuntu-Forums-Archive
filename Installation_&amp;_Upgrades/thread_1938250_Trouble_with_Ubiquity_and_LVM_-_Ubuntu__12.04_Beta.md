---
title: "Trouble with Ubiquity and LVM - Ubuntu  12.04 Beta 1"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by gcavalcante8808 on 2012-03-09
Hello all,

I'm trying to install the ubuntu in a new HD, that i have partitioned using LVM (pvcreate, vgcreate, lvcreate).

In the ubiquity partman i can see my volumes, choose, format, define the mount point, etc.

Then, i can insert my data (computer name, username, user pass, etc), but the installer 'freezes'(process seems to respond btw) but the status never changes, always showing the 'Removing conflicting operating system files'(idk if this is the correct status, im doing a installation in Brazilian Portuguese here, im asserting a simple translation against the en-us version) status message.

Does anyone have any clues about this problem?

I've tried to start ubiquity with -d and -pdb flags, but i havent see any stranger in the log (/var/log/installer/).

Thank you in advance.

Gabriel Cavalcante

PS: SInce i dont have OS yet, i dont have another OS CD here to continue the installation. (i really need to use this Desktop Default CD for 12.04)

---

### Post by marinara on 2012-03-09
how much ram do you have?
have you tried formatting the disk first?

---

### Post by darkod on 2012-03-10
Did you install the lvm package first? Since you say the partman can see the lvm I guess yes, but just to ask.

The standard desktop cd is not for lvm so you need to add the package first. Also, did you create separate /boot outside the lvm? You are aware that for lvm to work you need to have a separate /boot partition outside it, right.

---

