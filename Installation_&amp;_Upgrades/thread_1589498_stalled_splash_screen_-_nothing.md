---
title: "stalled splash screen - nothing"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by website.reader3 on 2010-10-06
After installing Ubuntu Lucid 10.04 from the CD, there was no grub boot prompt, the computer system boots Ubuntu directly up to the splash screen then freezes.

How do we fix this problem?

With the splash screen turned off it might be possible to localize the problem.  But no grub boot prompt was available to turn off the splash screen.

Now the system is frozen for as long as AC power comes to the power supply.

Any ideas?
------------
After the first post, here's what I've done

1. reinstalled Ubuntu allowing normal partition and extended partition to be build with a 2nd Ubuntu Lucid install.
Results? No success

2. removed all disk partitions and reinstalled Ubuntu as only one system on the normal partition (partition is marked bootable)
Results: No success

3. removed all partitions and formatting and boot flags, reinstalled Ubuntu from CD again
Results: No success, boot cannot even get to the boot table, but hangs signifying that the boot flags do work.

It appears that we're really dead in the water here on this machine for some reason.

I am going to attempt to grub my way to success on this machine, but it's going to take a lot of time to do this.
-------------
Found another oversight in the Ubuntu install package

If the Ubuntu CD on booting up finds a /swap partition, it mounts this partition even if the drive is going to be formatted later.
This block the formatting later, of course.  The "swapoff -a" command HAS to be used to free up this swap partition

Manual editing of the /etc/fstab file also had to be done, to remove the swap partitions and prevent a remount from occurring.

If any Ubuntu people are reading.. heads up here.
--------------
Things are getting more interesting, now the palimpest command refuses to edit the disk partitions

It spits out

MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=9
refusing to delete a metadata partition

and quits.

I tried palimpest under both normal user "ubuntu" and under superuser "su" but both times it gives up.
----------

Manually running parted, the disk partition editor resolved the problem.  Palimpest previously created an extended partition then created a swap space under that.  I had to use parted and 3 devs /dev/sda /dev/sda5 /dev/sda2 in order to lock onto the correct partition and delete them from the lowest order to the highest in their heirarchy.

I lost the mouse while doing this very critical procedure, and hopeful that the disk partition changes will successfully take before rebooting the system
-----------  more to come ----------

I manually edited the partitions on the first disk /dev/sda and after the partitions were (re)formatted, I then went to grub and attempted to turn off the splash screen as suggested in the Grub Tutorial [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

However rebooting the system /init 6 and hitting "shift" character continuously did come up to the grub menu, but the splash screen came up again when continuing on.

However this time, the system did successfully boot all the way up to runlevel 5

A check of the partitions (manually edited fstab for the boot partition /boot) showed them to be as expected.

I am going to file a bug report against the installer grabbing any and all swap partitions that it sees and indiscriminantly activating them, either in the CD run mode, or the actual run mode.  I believe that this is an oversight and not a common condition, but it forced me to manually tweak the partitions and reformat the disk drives which is not a task for the beginner.

---

### Post by ronparent on 2010-10-06
Hold down the left shift key during boot to bring up a grub boot menu (start holding before bios loading has completed).

---

### Post by nevius on 2010-10-06
What type of graphics card is in your computer?

If it is an nvidia card you may need to do the following after a fresh install of ubuntu.

1) hold down the shift key to enter the grub menu.
2) edit grub so that it has the boot parameter "nomodeset" before "quiet splash"
3) continue booting.

If this works, then add nomodeset /etc/default/grub and run the command "sudo update-grub" to make it permanent.

It may be a good idea to do a fresh install before trying this.

---

