---
title: "Adding fixed disk to SSD bootable box slows boot process"
date: 2019-03-08
forum: Installation &amp; Upgrades
---

### Post by 0cs935-bill on 2019-03-08
I installed 18LTS on a 250G SSD. The box boots in 5 seconds.

I then added a 500G fixed disk and mounted it at /home via fstab and now the box takes almost exactly a minute to boot. The fixed disk has a fresh partition and format with almost nothing on it.

Why the increased boot time?

---

### Post by oldfred on 2019-03-08
It should not be a minute, but slightly longer as it has to mount additional drive & partition(s).

Do your UUIDs all match? If not it either has to time out or fails to boot.
Does any ext4 partition need chkdsk which can make boot very slow as it may try to run it when booting.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 0cs935-bill on 2019-03-10
oldfred:

I never got notified of your reply. I thought I checked instant email ...

The URL from your suggestion is paste.ubuntu.com/p/CY68TQ4gv5/

The fixed disk mounts and is usable, so the UUID is correct. I double checked the UUID. The fstab entry I created is as follows:
UUID=blahblahblah       /home       ext4       defaults      0      0

Thank you

---

### Post by mc4man on 2019-03-10
> **0cs935-bill said:**
> I installed 18LTS on a 250G SSD. The box boots in 5 seconds.

I then added a 500G fixed disk and mounted it at /home via fstab and now the box takes almost exactly a minute to boot. The fixed disk has a fresh partition and format _with almost nothing on it._

Why the increased boot time?
What was your thought process about auto mounting your 2nd drive at /home?

---

### Post by 0cs935-bill on 2019-03-10
I was converting from a laptop to a desktop machine for a custom written point of sale system. I wrote it 13 years ago and it still keeps on ticking (I'm showing my age if you understand the ticking comment).

/home is where thousands of files get written daily. That would not be the best use of an SSD since it has a defined life for rewriting it's capacity. 

What I wanted the SSD for is a fast boot and rapid access to the dedicated POS application the box runs. The backup data it writes is almost never accessed but has to be kept for 5 years for the gov't regulators here on the island.

---

### Post by oldfred on 2019-03-10
Timex. :)

Report has not been fully updated to include all the NVMe drive info. So a lot of the data on NVMe drive is missing.
You are showing UEFI install to the NVMe drive and the old MBR(msdos) partitioning on sda drive.

When you created sda1 & made it /home, did you copy everything including hidden files from /home inside / on NVMe drive? Like this?
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Post this also:
cat /etc/fstab

---

### Post by 0cs935-bill on 2019-03-11
Strange that I got notified via email of mc4man's post, but not of yours. 

Let me back up a bit. When installing Ubuntu 18LTS, I can see no way to have it nuke/use multiple drives. Therefore, I installed on the SSD which means it allocated /home to the SSD. I would have preferred to install to both the SSD and the fixed disk at install time allocating /home to the fixed disk directly as it's less work for me.

I did copy everything at /home to another location, I believe /media, and then nuked everything under /home. Then mounted the fixed disk and transferred the moved /home contents to the drive. Maybe I messed that up, but all that was there was the bill directory, the default user (me), and the bill account works fine.

I don't see where a DOS partition should exist. I nuked the partitions on the fixed disk (old Fedora) and created a new partition (ext4). I noticed the reference to DOS myself and ignored it as inaccurate.



 bill@bill ~$ cat fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=23a73bc9-2699-44f1-9ca4-2a7b386ed59b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=78FD-5DC4  /boot/efi       vfat    umask=0077      0       1
UUID=1767b10f-24b7-4019-95e0-dcf54cdfefe9 /home           ext4    defaults          0       0
/swapfile                                 none            swap    sw                0       0

I was going to remove the reference to /boot/efi as it's useless but the delay issue took priority.

Thanks for your help. I'll read up on your other reference on how to move things properly.

---

### Post by oldfred on 2019-03-11
All I can think of is that you did not copy all the .xxx (hidden) user configuration files & it has to recreate defaults.
If UEFI install better to have all drives as gpt, not the old MBR(msdos), but not required.

Any line with # in fstab is just a comment, I normally leave those in, or even add my own so I know what I did when adding or changing entries.

Also if partition need fsck, boot can be slow as it will run that. Sometimes the basic fsck that boot process runs does not fully fix things and a full fsck is required.
       Must be unmounted:
Try "e2fsck -f /dev/sdb1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 

      
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mtodorov69 on 2019-03-13
Yes, when we speak about the slow boot, fsck on a fixed hard drive was my first idea as well.

---

### Post by 0cs935-bill on 2019-03-13
I'll try running a e2fsck, and if that doesn't clear this up I'm going to nuke the box and start over -- very slowly and deliberately.

I just partitioned and formatted that drive so I can't see where it would need it, but I'll do it anyway.

---

### Post by 0cs935-bill on 2019-03-14
The e2fsck found nothing. A reboot still took a minute.

Nuked the box. Used the 'something else' install option to put / on the SSD and /home on the fixed disk forcing a format on both.

Boots in 5 seconds now.

---

