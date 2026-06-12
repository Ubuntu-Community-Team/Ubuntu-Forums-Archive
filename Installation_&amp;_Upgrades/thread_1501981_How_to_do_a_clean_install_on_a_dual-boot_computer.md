---
title: "How to do a clean install on a dual-boot computer"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by ObamaLinux on 2010-06-04
I have been upgrading my Ubuntu partition faithfully with ever new release.  However, I've noticed it's been acting very sluggish lately and feel it would be better if I wipe it and do a fresh install.  Trouble is, my computer also has WinXP.  How do I go about it?

---

### Post by Revolutionary101 on 2010-06-04
Run your Ubuntu Live CD and use Gparted to delete your Ubuntu partitions. You will find an NTFS partition, DO NOT delete it. That is your Windows partition. You can delete all of the other partitions though.

When you reinstall Ubuntu, just select the largest continuous free space on your HDD to install on. That will just select the space that you freed up, by deleting the original Ubuntu partitions, to install Ubuntu on.

---

### Post by sites on 2010-06-04
WHOA!!! You do NOT need to delete every linux partition.  Or at least you might not need to.  Either way, make sure you have your data backed up.  Do you have a separate /home partition?  If so, just make sure you formate the / partition and all will go smooth.  The best partition scheme is to separate root and home with their own partitions.  When you re-install *buntu you just need to choose the same filesystem for your /home partition that it currently is.  But don't format it.  There are plenty of instructions for this kind of setup.

Let me state this clearly.  When installing Ubuntu, choose manual partitioning.  Don't go through the hassle of using gparted in a Live environment.  If your current installation isn't done this way, backup your /home folder before doing the following.

1) create the swap partition first using twice the amount of RAM you currently have
2) create the / partition using 10-12GB space and ext4 file system (or the file system of your choice)
3) create the /home partition with the remaining disk space and ext3 file system (or the file system of your choice)

With this scheme, any time you re-install *buntu you can leave your /home partition intact and use the same user name.  Then all your settings and files are right where you left them.

---

