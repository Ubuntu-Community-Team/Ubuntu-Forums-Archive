---
title: "Attempt to mount ntfs at /windows failed..."
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by slimjim83 on 2007-10-29
I'm trying to dual-boot WinXP & Ubuntu 7.10 on a new hard drive.  Its a 160GB drive set up as follows...
Partition #1 - ntfs -- WinXP Pro already installed (53.7 GB)
Partition #2 - ext3 -- will be root "/"  (53.7 GB)
Partition #3 - swap (2.1 GB)
Partition #4 - fat32 -- mounted at /share (50.5 GB)

I'm using the minimal CD, and when it comes to the partitioning section of setup, this is what I get.

"The attempt to mount a file system with type ntfs in IDE2 Master, partition #1 (hdc1) at /windows failed.
You may resume partitioning from the partitioning menu.
Do you want to resume partitioning?"

I have also tried mounting it as "/win" which failed, however it worked at "/media/windows".  I do not want to mount it in this location, and I can't seem to find any answers on how to resolve this.  If I need to I can re-install windows, but I don't really want to spend the time.

Any help is appreciated...

---

### Post by taurus on 2007-10-29
First of, do you have a partition called /windows?

Then, what command did you use to mount your ntfs filesystem?

---

### Post by slimjim83 on 2007-10-29
This is all in the initial setup of Ubuntu.  The Windows partition (Part #1) has Windows installed and it is functional (I have been using it for a couple of days).  The screen I am getting is inside the setup program itself, during the partition section.  I am choosing to set up the partitions manually, since they are already created.  All partitions were created using QParted, then I installed Windows to the first partition, now I am trying to install Ubuntu to Partition #2.

Reminder that I am using the Minimal CD, NOT the normal Live CD.

Thanks
slim

---

### Post by slimjim83 on 2007-11-02
Does anyone have any ideas why I'm having this problem??

EDIT: Could it have anything to do with the Windows partition being set as bootable?

---

