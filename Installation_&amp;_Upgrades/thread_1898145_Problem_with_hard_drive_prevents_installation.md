---
title: "Problem with hard drive prevents installation"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by Lyalpha on 2011-12-20
I thoroughly messed up a bunch of files in my hard drive trying to fix a problem where the filesystems wouldn't mount.  I formatted the hard drive but Installation of 10.04 from a disk fails saying there is a syntax error in some line of a file /init/scripts/functions I think.  That doesn't matter though.  I just want to now what I have to do to the hard drive to allow the 10.04 boot disk to install 10.04.  Does the hard drive need to be completely wiped instead of formatted?

---

### Post by darkod on 2011-12-20
You should always be able to install even without formatting the hdd. Are you sure the CD hasn't developed a fault, a scratch, etc?

Can you boot in live mode with the CD?

---

### Post by Lyalpha on 2011-12-20
Maybe I didn't format correctly.  How would you do it?  I can't boot a live cd either.  I am currently using knoppix to boot from the cd drive.  There is no scratch on the cd.  Installing from a usb doesn't work either.

---

### Post by darkod on 2011-12-20
But can you get to a ubuntu live mode to open Gparted? Much better to use a GUI tool for partitions managing.

If you can, simply select the hdd in Gparted, and then in the menu Device - Create Partition Table... Leave the type as default, msdos.

That will write a new blank partition table.

WARNING: That will delete all data on the disk, but I think you already know that and there is nothing you need on the hdd.

---

### Post by Lyalpha on 2011-12-20
Im using knoppix not a ubuntu live cd.  I can't get anything to mount to the hard drive, not even a live cd.  It doesn't have gparted.  It has parted though, although I'm not sure how to use it.  I suspect it's not intuitive.

---

### Post by darkod on 2011-12-20
According to the parted manual, you need to do:

- under assumption your hdd is /dev/sda, to write new msdos table and then exit parted execute:

sudo parted /dev/sda
mklabel msdos
quit

---

### Post by Lyalpha on 2011-12-20
msdos is invalid token it says.

---

### Post by Lyalpha on 2011-12-20
I just deleted all the partitions on the drive with fdisk and made a new one.  I even formatted the new one to be sure.  I still can't install from a disk or a usb stick.

---

### Post by Hakunka-Matata on 2011-12-21
Are your troubles consistent?
Or is the problem changing every time you reboot?
I'm wondering if it may be a hardware problem, loose drive cable, loose screw in the belfry?
But then Knoppix works fine you say, sounds specific to the hdd?, no?

---

### Post by Lyalpha on 2011-12-21
It's consistent.  It's definitely not a hardware problem.  I would guess that it is a scratched disk but the usb installer doesn't work either.

---

### Post by darkod on 2011-12-21
Any chance to create a usb with a newly downloaded ISO?

If you can't boot at all it doesn't seem related to the hdd.

---

