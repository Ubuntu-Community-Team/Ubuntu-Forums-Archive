---
title: "Drive disappeared on Flash drive install."
date: 2023-10-09
forum: Installation &amp; Upgrades
---

### Post by rick-price on 2023-10-09
I went to install a copy of the latest LTS release on a Dell Laptop for my daughter.  I downloaded the iso file, merged it to the memory stick with Rufus, Restarted and it began to load.  I selected the 'Install Ubuntu' option from the install screen and it progressed until I got to the screen where it needs to know where to put the files.  It has deleted or unmounted the disk and I'm not sure of how to find it or remount the drive for use.  I've done this at least 30 times for people and never had this issue before. 

Everything else appears to be working fine and I can use Ubuntu from the memory stick.

Any help appreciated.

Rick Price

---

### Post by yancek on 2023-10-09
Does this Dell laptop currently have anything (another OS) on it?  Is it a newer UEFI machine?  Did you boot in UEFI mode if so?
Go to the link below and about half way down the page, you will see the Installation Type screen.  Do you get to that point?  If so, does it show any drives or partitions?  A simple explanation would be that the machine has a windows OS installed and it would have been left in a hibernated state.  If that is the case, you need to boot windows and disable hibernation temporaily.

Can you boot the Ubuntu install media and select Try Ubuntu, then open a terminal and type:  sudo fdisk -l  which will list drives/partitions.  If there is no windows installed, do you get any information from fdisk?

---

### Post by rick-price on 2023-10-09
There was Win10 on there when we started.  I had disabled UEFI in order to get it to let me change the boot order and use the memory stick.  Doing fdisk -l shows 9 loops (/dev/loop0 - /dev/loop9)  They are all relatively small and then there is the USB stick as one as well.  It is the only one showing a partition table.

When booting without the USB stick, I get a dell diagnostic that tells me there is no hard drive installed.

---

