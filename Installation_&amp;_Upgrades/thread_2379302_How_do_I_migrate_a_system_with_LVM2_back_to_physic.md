---
title: "How do I migrate a system with LVM2 back to physical partitions"
date: 2017-12-04
forum: Installation &amp; Upgrades
---

### Post by r_widell on 2017-12-04
This is not technically an installation question, so if there's a better place to post this, please advise.

I recently had a hard disk crash on a 16.04LTS system (Kubuntu, if it makes a difference) that I had installed on two drives using LVM2. One drive had an ext4 partition mounted as /boot, and the second partition as one of the two PVs in a single VG. The entire second drive was the second PV in that VG.

I have backups, both as a Clonezilla image of the entire system in addition to tar archives of the individual filesystems.

But I discovered that one of the negatives of a system configured with LVM2 is trying to determine WHICH drive is failing when you have multiple PVs in a VG.

So I decided to migrate the system to a standard configuration with physical partitions for each filesystem, using the tar archive restored to a new drive.

The problem I'm having is getting the old system to boot. It keeps trying to load up the (now non-existent) VG, and eventually halts at a busybox prompt.

During the boot process it keeps trying something called ```
/scripts/local-block
``` I've searched for the local-block file and for the scripts directory to an avail.

I've tried making a new initrd after disabling the lvm entries in rc[0-6,S].d but that didn't help.

What do I need to do to make this system forget about the non-existent VG and just mount the fs listed in /etc/fstab?

Thanks,
ron

---

### Post by r_widell on 2017-12-05
The actual problem turned out to be grub
One of the boot arguments to the kernel placed by grub was ```
root=/dev/mapper/<VGname>-<LVname>
```
After I changed that to ```
root=LABEL=<rootfslabel>
```it booted fine, with no references to <VGname>.

Just though you might like to know.

ron

---

