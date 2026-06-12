---
title: "Default Install Partition"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by Conquerer on 2004-10-25
I have already set up a 8Gb partition to install Ubuntu. However, when I get to the "Partition" section of the install, it is not clear on exactly which partition the new filesystem will be installed. I have Windows Xp on HDA1, and I just want to be sure that it wont get overwritten. How do I specify which partition I am installing on?

---

### Post by JProgrammer on 2004-10-25
You have to do a "Manually edit partition table" in the Ubuntu installation process this program will show you your current partition table just set up '/' (root) on that 8 gig partition you have and don't forget to set up a swap partition too

---

### Post by FLeiXiuS on 2004-10-25
Auto-Partitioning will partition your drive in a way where it selects from either free'd space or other linux partitions on the drive.  You may choose.   It then formats to a considerable filesystem(ext3/swap).  

Note: By default only / is mounted.

Keep in mind what **JProgrammer** said.

---

### Post by JProgrammer on 2004-10-25
But we all know you want reiserfs instead of ext3  :twisted:

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=JProgrammer]But we all know you want reiserfs instead of ext3  :twisted:[/QUOTE]

But of course!  :-)  I love my partitions!

/dev/hdb5 on / type **reiserfs** (rw)
/dev/hdb1 on /boot type **reiserfs** (rw)
/dev/hdb6 on /home type **reiserfs** (rw)
/dev/hdb7 on /usr type **reiserfs** (rw)
/dev/hda1 on /drives/c_drive type _ntfs_ (rw,uid=1000,gid=1000,umask=0000)
/dev/hda5 on /drives/z_drive type _ntfs_ (rw,uid=1000,gid=1000,umask=0000)

:-)

---

### Post by JProgrammer on 2004-10-25
rw ntfs you are game

---

