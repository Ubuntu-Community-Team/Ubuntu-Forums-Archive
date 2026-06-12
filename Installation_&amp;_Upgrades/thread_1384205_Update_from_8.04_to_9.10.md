---
title: "Update from 8.04 to 9.10"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by insp on 2010-01-18
Dear All 
 
I am using Ubuntu 8.04 and windows XP sp3 dual boot on my dell inspiron laptop and there is no problem.
Now i want to update from 8.04 to 9.10 without removing windows xp from system i.e. i want to install 9.10 on the place 8.04 without removing windows xp. please help

---

### Post by tachuela on 2010-01-18
Use Gparted Live CD; get rid of everything after Windows; then install Ubuntu.

---

### Post by Cheezespread on 2010-01-18
**_If you want to upgrade the Ubuntu over internet_**

Yes , you can do it . But a direct install from 8.04 to 9.10 is not possible as I understand. You will have to do an incremental upgrade to 9.10. That means , you will have to pass every Ubuntu release in between and then finally upgrade to 9.10 from 9.04 .

**_Do a fresh install _**

A bit too much of a hassle at times for me ( I am still learning ) . What I always end up doing is removing the Ubuntu partition from Windows and then rescue windows ( Phew !! ) using something like SuperGrub. Then you can do a fresh installation of 9.10 . It's not as scary as it sounds ;-) .

---

### Post by audiomick on 2010-01-18
you can update 8.04 > 8.10 > 9.04 > 9.10 using the updater,

or

re-install using the installer CD.

In either case, backup important stuff before you start.
Get a live CD and see how your computer runs booted into the CD using the "try without changing" option.

If you re-install, bear in mind that everything in your installation of Ubuntu will be lost (XP will not be touched, as long as all goes well)
unless you have /home on a separate partition. If that is the case, you can simply re-mount /home in the new install,  thereby retaining your data and settings. You might want to think about creating a separate /home partition before you start.
here is a guide for that
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

When you re-install, I think the installer will allow you to take the space that the current install is occupying without any bother.

Because I like to do things step by step, so I can see what's happening, I would do it like this: ( I am assuming a separate /home partition)

Backup anything important from both OSs.

Boot into the live cd and start gparted
system> administration> gparted

use that to remove the old system partition.

Run install and choose manual partitioning when the time comes

Create a partition mounted at / for the new system.
Remount the old /home at /home without formatting.
Remount the old swap partition.


this should get you where you want without any problems

---

