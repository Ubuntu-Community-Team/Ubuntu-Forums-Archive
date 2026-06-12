---
title: "Installing grub to partition during install"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by venkmanT61 on 2007-10-21
I was searching for a few hours (unsuccessfully) to verify whether the UBUNTU install cd allowed specific location for GRUB bootloader install. 

Well, it does. I thought I'd share the information so it is "ubuntu" of me :)

Case Description:
XP on a T61 thinkpad with Rescue and Recovery (RR) Partition

Goal: to add ubuntu as a boot option within XP, and not destroy the RR partition.
Also, to not destroy the thinkvantage functionality at boot time
Therefore, the effect is to add ubuntu and have grub be installed into the partition not the MBR of the drive.

How To:

Just before pushing the "Install" button on the "Ready to Install" page, you get a summary of what partitions etc are to be populated with what.

Select the "Advanced" button
The text says that grub will be installed onto: (hd0)
This would be the MBR of the drive, accepting this you'd blow your XP boot.

Not selecting this option means (IMO) that you have to boot from linux rescue cd, then manually install grub on the correct partition and all that jazz.

Here's what you do:
Note: At this point I am assuming that the drive has been partitioned (as it should have in previous steps - unless I am mistaken, if so someone comment and let ppl know).

open a terminal
type in: fdisk /dev/sda
(or whatever the main harddrive is called for your hardware)
and perform a "p" for print
my partition on the T61 looked like:

/dev/sda1 * .... HPFS/NTFS
/dev/sda2   ......  Compaq Diagnostics
/dev/sda3 ..... Linux
/dev/sda4 ...... Extended
/dev/sda5 ...... Linux Swap/Solaris
/dev/sda6 ...... Linux

I had designated my sda3 as root (/) and sda6 as /home
So, my goal was to get grub into sda3
in grub "talk" first harddrive = hd0 (as was displayed in advanced options)
and partitions count from 0 instead of 1
so sda3 = (hd0,2)

Once the install finishes, the system boots into XP agnostic of the linux beside it.
Once into XP, download bootpart and follow the very clear steps in the bootpart.txt file
I'd suggest go straight to the example it is extremely clear as to what you need to do.

Reboot after you have successfully installed ubuntu into the XP Boot.ini
This time XP boots with a menu to allow selection into ubuntu.

So, now you have XP, saved the RR partition, saved the thinkvantage blue button magic
have yourself a 64bit ubuntu (which can now access all of my 4GB of ram :) )

Good Luck.

---

