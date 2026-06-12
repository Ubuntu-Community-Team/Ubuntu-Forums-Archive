---
title: "How do I delete or wipe the HD for a new installation?"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by tuproxy on 2007-12-16
I had 6.10 installed and ran into some problems.  I decided to install 7.04 and now am getting a GRUB error.  I want to wipe the hard drive and start over.  it is a SATA drive and I can't use my one utility as it only accepts IDE and SCSI drives.  

Also is there a way to install in text mode instead of booting to the Live CD with 7.04?

---

### Post by torgrot on 2007-12-16
You can download gpartd, burn it to CD and boot off of it  Then use that to delete your partitions and repartition you drive before installing.  You could boot with the alternate CD to install in text mode.

torgrot

---

### Post by logos34 on 2007-12-16
you don't even need to download gparted live cd--just use the version on the install cd (>system>admin>gnome part editor)

although the newest version (0.3.4) of gparted live cd can do a couple of things the earlier ones can't

---

### Post by ajgreeny on 2007-12-16
I think gparted is on the Ubuntu Live CD you already have so you shouldn't need to download the Gparted live CD.
>  I can't use my one utility as it only accepts IDE and SCSI drives.  I'm not quite sure what you mean by this, but parhaps your problem is that Ubuntu Live CD can mount the hard disks at boot time meaning you can't format them.  Surely all disks are either IDE or SCSI, (Pata or Sata) so I'm baffled.

Make sure the hard disks are unmounted and trya again with the live CD to format the disk or at least delete the partitions on it and then install however you want.

---

