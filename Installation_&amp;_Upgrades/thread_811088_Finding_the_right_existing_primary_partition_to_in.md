---
title: "Finding the right existing primary partition to install Ubuntu into"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by oserdavid on 2008-05-28
I've played around with Hardy Heron via Wubi - and I like it, except it's the amd64 version, which has some problems. I'm now ready to take the plunge and install Ubuntu 8.04 i386 version directly. But ending up with a dual boot system. I've burned 8.04 onto DVD, and it works. However, I had to abort installation because I couldn't figure out my partitions. 

This is because I have Vista Business OS on a Tosh with Disk0 (Toshiba) with 3 partitions - the two main ones being Primary partition Vista C: and Data F: - they are each around 74 GB.

Data F: is empty - and that is where I want to install Ubuntu.

To complicate matters the machine also has a Hitachi logical drive, Disk1, around 160GB which Windows calls D: where I actually keep my Windows applications and data that don't need to be installed in C:

When I get to the partitioner bit of the installation, I have difficulty distinguishing between what Windows calls C: and F: - I think I've spotted D: from the size description - so I know to avoid that. 

Can any guru out there help me to avoid installing Ubuntu into C: and help me to install it into F? I cannot really make head or tail of the Linux descriptions of these two existing primary partitions which are about the same size - especially as the numbers under the 'used' heading don't really correspond with what I see as 'used' under Windows.
David :confused:

---

### Post by iaculallad on 2008-05-28
Using the GParted which comes with the LiveCD is pretty simple. Locate and DONT touch the drive where your existing vista OS resides, usually with NTFS as a filesystem. If you're sure that drive F is empty (usually indicated by blank value under the "Used" column in your Gparted), that's where you create your for Swap, /, and /home partitions. Use "Manual" partitioning and not "Automatic" partitioning.

---

### Post by Slim Odds on 2008-05-28
> **iaculallad said:**
> Using the GParted which comes with the LiveCD is pretty simple. Locate and DONT touch the drive where your existing vista OS resides, usually with NTFS as a filesystem. If you're sure that drive F is empty (usually indicated by blank value under the "Used" column in your Gparted), that's where you create your for Swap, /, and /home partitions. Use "Manual" partitioning and not "Automatic" partitioning.

If the drive shows as F: in Windows, it will not show as unused in GParted.

If it has a drive letter, that means it's NTFS (or FAT32).

---

### Post by iaculallad on 2008-05-28
> **Slim Odds said:**
> If the drive shows as F: in Windows, it will not show as unused in GParted.

If it has a drive letter, that means it's NTFS (or FAT32).

Yap, it will not totally show as unused, but with the highest amount of free space (as said that it's empty). You're drive F don't show as F in Gparted though, it would either be in hda or sda in either case. Do the command **sudo fdisk -l** to see it for yourself.

---

### Post by oserdavid on 2008-05-29
Thanks iaculallad and Slim Odds - C, F and D are all NTFS. And as long as 'used' really does mean 'already used' then I guess it will be safe to manually select the drive with roughly the right size (they do not, unfortunately, correspond exactly with the Windows-displayed sizes) and the smallest amount 'used'. Then hope for the best... (at least I am backed up!)
David

---

### Post by oserdavid on 2008-05-30
Thanks again guys.
Unfortunately, using 'manual' failed, as, after I had created the first partition, I think as directed, the remainder of the 'free' space became 'unusable' for some reason. I therefore tried one of the guided automatic options on my 160GB 'Logical' drive (D), which contained my data and applications - but not Vista (which is on C),and had a very lucky escape. It left me with a very small D drive under Windows, and took over nearly all of my otherwise empty F drive. Fortunately, it left my Windows applications and data intact I found out after rebooting, and I was able to expand D significantly again under Vista - turning it into a 'dynamic' drive - whatever that means! Windows, in the meantime, needed to run a chkdsk and do some repairs. But as far as I can tell, no serious damage has been done and I now have a dual boot system with both OSs working well (so far). I think I have been very lucky - and I wouldn't recommend anyone else to do what I did. I just wish the manual method hadn't failed the way it did. Just to help anyone else - does anyone know why 50+ GB on the (what Windows calls) F drive became 'unusable' for the manual method, after the first bit of partitioning by Ubuntu 8.04 partition manager? I have to say - he whole thing proved very user-unfriendly (not to speak of the whole saga of getting my mic to work properly under Hardy Heron - another story!!)
David

---

