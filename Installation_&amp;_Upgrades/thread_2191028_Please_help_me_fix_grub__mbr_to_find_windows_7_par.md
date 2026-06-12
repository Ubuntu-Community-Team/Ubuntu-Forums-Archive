---
title: "Please help me fix grub / mbr to find windows 7 partition"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by glennthompson1971 on 2013-11-30
I cloned Windows7 to a SSD but cannot boot it. I installed Ubuntu 13.04 to a second SSD, but grub doesn't see Windows7 partition.
Can you help me fix so I can dual-boot?

Here is what I did:
--------------------------

I have a (spinning) 1TB SATA drive which has Windows 7 (/dev/sda3) and Ubuntu 12.04 (/dev/sda4) installed.

I bought two SSD drives: a 250GB drive that I want to put Windows on, and a 120GB drive that I want to put Ubuntu 13.04 on.

I decided to clone Windows7 from /dev/sda3 to the 250GB SSD. I did this using EaseUS To Do. It seemed to work ok.
I couldn't clone the whole of /dev/sda to the 250GB SSD because it has 1TB on it.

When  I unplug the original /dev/sda and switch the 250GB SSD to be /dev/sda,  the computer just hangs on reboot, flashing a cursor.
So clearly not finding any boot section.

So  then I connected my second SSD (120GB) as /dev/sdb and install Ubuntu  13.04 from a USB pen drive, figuring maybe grub would be
smart enough to discover the Windows7 partition. Alas it did not.

So after booting into Ubuntu 13.04 off the SSD, I added a file /etc/grub.d/11_Windows which contains:
#! /bin/sh -e
echo “Adding Windows” >&2
cat << EOF
menuentry “Windows 7&#8243; {
insmod ntfs
insmod chain
insmod drivemap
set root=(hd0,0)
drivemap -s (hd1)(hd0)
chainloader +1
}
EOF

Then I ran sudo update-grub.

Upon reboot there is no Grub menu and it boots to a terminal only (no graphical login), with the mouse disabled.

Upon a second reboot, there is still no Grub menu, but it boots back to Ubuntu and all works fine (Ubuntu works fine,
but still cannot boot to Windows, though Windows partition can be mounted from Ubuntu fine).

For all of the above I've been depending on Google searches to help me along, so I'm out of my depth. 
HOW DO I BUILD A GRUB MENU ON MY SYSTEM SO IT DISCOVERS AND ALLOWS ME TO BOOT INTO
MY WINDOWS PARTITION?

My original /dev/sda - the 1TB spinning drive - is still intact with Windows7 and Ubuntu partitions, but is disconnected.
Windows7 was on partition 3 on that drive, but is on partition 1 on the 250GB SSD.

I can mount the Windows7 partition from the 250GB SSD fine under Ubuntu and I ran bootinfoscript which told me that
grub2 is installed in the MBR of /dev/sda. 

The link: 
[http://paste.ubuntu.com/6500343/](http://paste.ubuntu.com/6500343/)
gives all details about my system, including results of fdisk -l etc.

Can anyone help me get to the point where I can dual-boot to Windows7 on /dev/sda1 and Ubuntu on /dev/sdb?
I don't think I have the original Windows7 DVD (this is a Dell PC and it came pre-installed).

Thanks.

---

### Post by oldfred on 2013-11-30
I do not know all the details of Windows. It does not like to be moved, even if on same system. It may still want a new update as it sees different hardware. 
But you did not copy it correctly as you are missing the 100MB boot/repair partition. Windows 7 normally installs to two partitions with two main boot files in the 100MB boot partition. You have no bootmgr nor BCD.

You may be able to use a Windows repairCD or flash drive to fix your install as it will work from one primary partition with the boot flag. Make sure you have BIOS booting from sda before running repairs, otherwise it may overwrite 100MB of sdb.

Install grub to sdb and confirm you can boot from it in BIOS. As the Windows repairs will put a Windows boot loader on sda. And that is ok, if you can boot Ubuntu from sdb. But change BIOS back to sda before the Windows repairs.
If in Ubuntu or you can use Boot-Repair, but do not use auto fix, but in Advance choose Ubuntu install and choose sdb.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

