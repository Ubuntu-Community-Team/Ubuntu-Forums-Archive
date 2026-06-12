---
title: "Installing from hard drive"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by Karl1982 on 2010-10-05
Something I do with computers I set up from time to time is create my own recovery partition.  I find this is particularly useful on a test box or one I'm setting up to give to someone.  I've been able to do this with Windows a couple different ways, and while I'm sure it's very doable with Ubuntu... I'm just not quite sure how.  Right now my drive for this is I want to install Ubuntu on some old machines that don't boot USB, and I'm out of CDs, but I do have my trusty USB to IDE/SATA adapter.  I can partition and preload whatever I need.

Typically I'll make a 1GB partition at the end of the drive and drop in whatever OS source or other utilities I intend for it to have, and set it all up with grub4dos in the MBR.  In fact, I often keep grub4dos boot files in there as well.

I tried copying the files from the CD to such a partition, and while I was able to boot to it and start the installation, it failed saying it couldn't find the CD.  I also tried something with unetbootin to treat the hard drive like a flash drive... I don't remember which option I picked, but whatever it was, it didn't work.

So, what can I do with this?

---

### Post by oldfred on 2010-10-05
I did this but on a USB flash drive and it works. I would think you can loop mount and install as long as the partition you install from is not mounted.

Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

