---
title: "Changing device names (Hardy 8.04)"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by amsterdamsky on 2008-08-05
I'm having a problem with drive names changing after I reboot.

My system is an AMD64 machine with 6 drives: 1 SATA drive for the system, 4 SATA drives for a software RAID via mdadm, and 1 IDE drive for backups.

In its previous incarnation as a gentoo box, the SATA drives showed up as /dev/sda through /dev/sde and the IDE drive was /dev/hda

Now that I've installed Ubuntu, the IDE drive shows up as a /dev/sdX type device and the really perplexing thing is that it changes after each reboot!  Sometimes the IDE drive gets /dev/sdb, sometimes /dev/sdf.  In each case the 4 SATA drives that make up my RAID are always consecutive, and the IDE drive is either at the beginning or at the end.

The problem is that the mdadm configuration is expecting drives b through e for the RAID and when the IDE gets b, the RAID drives are then c through f and the RAID doesn't start.

Anyone have any ideas as to how to get the device names to "stick" after reboots?

---

### Post by tamoneya on 2008-08-05
im not certain how to make them "stick" but the simple way to deal with it is to reference the drives by their UUID instead of their device node.

[http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid](http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid)

---

### Post by amsterdamsky on 2008-08-05
Good idea... same problem though...  the UUID stays the same but the device name alternates between /dev/sdf1 and /dev/sdb1

The raid configuration file (mdadm.conf) uses device names to indicate the raid drives and not UUIDs... if it did, then my problem would be solved, but I can't find any indication that mdadm could use UUIDs instead of device names

---

### Post by lvm on 2008-08-06
Same problem here - AMD64, heron, md raid had to be reassembled manually after each reboot. Damn.

---

### Post by xen-uno on 2008-08-06
What is the contents of your **/media** directory? What you will see is directories that act as mount points (for NTFS and CD-ROM's in my case). I had indirect duplicates in mine, that is, there would would be a folder called **sda5**, but also another called **data**. They both pointed to the same partition. Deleting all the sdXX's where a clone volume labeled folder existed corrected my problem. It also had a plain **CD-ROM** in there that was handled by **CD-ROM0**.

---

### Post by amsterdamsky on 2008-08-06
Looks like the fix for this is to set your mdadm.conf to automatically select the right raid drives:

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

This did the trick for me... then use the UUID to mount /dev/md0 where you need it.

---

### Post by stepdown on 2008-08-11
> **amsterdamsky said:**
> # by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>Could you explain what this is doing? Does it allow you to do everthing by UUID rather than SDA name?

---

