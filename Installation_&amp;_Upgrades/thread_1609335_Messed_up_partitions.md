---
title: "Messed up partitions"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by hathiphnath on 2010-10-30
Hi all!

After updating to 10.04 LTS, my partitions went all weird (see the screenshot).

I'd like to merge sda5 and sda7, as they were before the update. What should I do?

Thanks!

---

### Post by q999 on 2010-10-30
try [http://partedmagic.com/](http://partedmagic.com/)  a free  live cd /linux / you may have to copy any data / repart /paste ////  or you can/ just delete all linux partitions (saving windows)and then install ?? linux...
you could do this with an ubuntu live cd and that partion manager but I think a disk with parted majic and [http://clonezilla.org/](http://clonezilla.org/) are the best disk tools you can get,and the best part their free..

---

### Post by hathiphnath on 2010-10-30
Basically a reinstall is the only option?

---

### Post by Rubi1200 on 2010-10-30
I am not sure if that is the only option, but how exactly did you end up in this situation?

Also, you need to do some research, but I don't think it is possible to merge 2 partitions with different file-system types; in this case sda5 is marked as ext3, sda7 as ext4.

Certainly, you need to backup/clone the partitions before making any more changes.

---

### Post by viralmeme on 2010-10-30
> **hathiphnath said:**
> After updating to 10.04 LTS, my partitions went all weird

That's the first time I heard of an update messing up partitions

---

### Post by hathiphnath on 2010-10-30
> **Rubi1200 said:**
> Certainly, you need to backup/clone the partitions before making any more changes.Definitely.

> **Rubi1200 said:**
> I am not sure if that is the only option, but how exactly did you end up in this situation?It's not my own PC and I was not present when the update was made, so, I don't really know how it was brought down to this. :( All I know it was "updated".

> **Rubi1200 said:**
> Also, you need to do some research, but I don't think it is possible to merge 2 partitions with different file-system types; in this case sda5 is marked as ext3, sda7 as ext4.I've no problem with reformatting the ext3 partition. All it has on it, is the previous Ubuntu installation with all the home/user files moved to the new partition (sda7). I simply thought of deleting sda5 and expanding the sda7 over the newly created unallocated area, but sda5 was marked as a boot drive, so, it complicated things.

---

### Post by Rubi1200 on 2010-10-30
Are you able to get us the output from the following commands?:

```
sudo fdisk -l
```

```
sudo blkid
```

```
cat /etc/fstab
```

Thanks.

---

### Post by hathiphnath on 2010-10-30
```
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = silindrit of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeee5d2c3

    Seade Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13054   104856223+   7  HPFS/NTFS
/dev/sda2           13055       38913   207712387    5  Extended
/dev/sda5   *       13055       25842   102719578+  83  Linux
/dev/sda6           37860       38913     8466223+  82  Linux swap / Solaris
/dev/sda7           25843       37524    93835633+  83  Linux
/dev/sda8           37525       37859     2688000   82  Linux swap / Solaris
``````
sudo blkid

sudo: unable to resolve host Xxx
/dev/sda1: UUID="B470CFFA70CFC17A" TYPE="ntfs" 
/dev/sda5: UUID="5a5f123a-abfb-408c-98b5-0dd3f202b11d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="71240eb8-a657-415e-b02a-27d5466bf68d" TYPE="swap" 
/dev/sda7: UUID="bc54e17e-3c27-4a49-ab36-5142a50544fe" TYPE="ext4" 
/dev/sda8: UUID="aee60218-58ad-43fa-b68d-9d857d3b6e70" TYPE="swap" 
``````
cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=bc54e17e-3c27-4a49-ab36-5142a50544fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=aee60218-58ad-43fa-b68d-9d857d3b6e70 none            swap    sw              0       0
```

---

### Post by Rubi1200 on 2010-10-30
Thanks for the output hathiphnath.

I understand why you were concerned about deleting sda5 because of the boot flag.

```
/dev/sda5   [COLOR=Red]*[/COLOR]       13055       25842   102719578+  83  Linux
```However, since you did a clean install on sda7 > / was on /dev/sda7 during installationthere should be no problem deleting sda5 and expanding sda7 into the space it occupied.

Again, make sure you have backups before you start.

In the worst case scenario, we may have to reinstall GRUB, but that is easily accomplished.

---

### Post by hathiphnath on 2010-10-30
> **Rubi1200 said:**
> However, since you did a clean install on sda7 there should be no problem deleting sda5 and expanding sda7 into the space it occupied.Thanks! I'll try it out.

---

### Post by WestCoastSuccess on 2010-10-30
Don't want to hijack this thread, so have deleted my post and established a new thread elsewhere.

---

