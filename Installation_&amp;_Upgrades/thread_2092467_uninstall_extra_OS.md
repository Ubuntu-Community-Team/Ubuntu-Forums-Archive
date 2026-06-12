---
title: "uninstall extra OS"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-12-07
I have ubuntu,kubuntu and xubuntu installed alongside each other, each on it's own
25 gb partition.
I would like to delete kubuntu and xubuntu and keep ubuntu as the only OS.
    What is the safe procedure for doing this?  Any time i have deleted a partition before i
have always messed something up, usually losing everything.

I do have ubuntu set as default boot.  All help appreciated.
edit; i should mention, these are 3 logical partitions within an extended partition.

---

### Post by Bucky Ball on 2012-12-07
You need to know which install is running the show, namely which install's grub is being used to give you the menu at boot. If you intend to kill the install which is running grub you'll need to research how to reinstall it from the Ubuntu that's left.

Easiest way of getting rid of the other two partitions is boot from the LiveCD, launch Gparted partition manager, make sure the partitions you want to delete are unmounted, delete them.

This will leave you free space to either expand an existing partition or create a new one. Bear in mind that four primary partitions is the max. Don't know how you have things set up but three partitions and expanded partition which can hold as many logical drives as the hardware can handle is one way to go.

Good luck. ;)

---

### Post by offgridguy on 2012-12-07
Thank you for the reply. Here is a screenshot of the setup.
edit; I did set the default boot using this advice from oldfred.
> 
Which ever one you install last will be the default boot, but you can easily change that by booting into which ever install you want as default and run this:

sudo grub-install /dev/sda 
It does boot direct to ubuntu now, no menu choice.

---

### Post by Bucky Ball on 2012-12-08
If you hit shift after the BIOS screen you should get to the menu.

Oldfred is correct; that is the command you need to reinstall grub, but the last install is not necessarily the one that is running the show, depending on how you went about installing its grub (which partition is it installed on?).

I see you have two EXT2 partitions and a heap of unallocated space there. You still have all installs? I'd make a plan about how you want to set things up before going ahead with it.

---

### Post by offgridguy on 2012-12-08
Thank you, Bucky Ball,
I still have all the installs,  the ubuntu i want to keep is on /dev/sda5
which is what boots up when i start.
Thanks for the tip about shift.

---

### Post by Bucky Ball on 2012-12-09
All good then. Kill sda6 and everything above it, make a big data partition and re-create the swap on a 2Gb partition at the end and you're sweet. Good luck. ;)

Naturally, if you have any personal data in the other two installs (say, in their /home directories) back it up or save it to the /home directory in sda5.

---

### Post by offgridguy on 2012-12-10
Thank you again , Bucky Ball for all your help.

---

### Post by Bucky Ball on 2012-12-10
No probs. That's why we're here. Hope all goes well. ;)

---

