---
title: "Reinstalled 14.04 LTS"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by azdavef on 2016-01-30
I thought I had a major problem with my installation and decided to do a fresh install of 14.04 LTS (dumb, I know).  After choosing to remove the current installation and installing from the live CD, I now have two volumes listed for the drive. I have a 105 gb volume that has all of my previous folders and a 6.4 gb volume with the new installation.  I have a dual drive, dual boot machine with Windows 10 installed on the other drive.  I don't want to lose the Windows drive and I do have a back in time backup from yesterday.  Could someone suggest a solution?

---

### Post by azdavef on 2016-01-30
I deleted the "extra" volume with GParted from the live CD and reinstalled.  Everything worked as advertised.

---

### Post by grahammechanical on 2016-01-30
Are you sure that you did not delete the swap partition? If we direct the installer to install Ubuntu to a hard drive using the Erase disk and install Ubuntu option it will create at least 2 partitions. One for Ubuntu and one for swap.

Regards

---

