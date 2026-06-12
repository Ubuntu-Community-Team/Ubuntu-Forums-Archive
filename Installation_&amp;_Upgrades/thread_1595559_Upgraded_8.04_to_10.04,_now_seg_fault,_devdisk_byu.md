---
title: "Upgraded 8.04 to 10.04, now seg fault, /dev/disk /byuuid/ddf7a... does not exist"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2010-10-13
The upgrade went without incident until I rebooted. Then the Grub boot sequence showed only the old 8.04 and XP options and no 10.04 option. The system boots to XP fine, but booting to 8.04 gives a seg fault saying that:

/dev/disk /byuuid/ddf7a82e-ebca-4dfe-b571-6bb568be614d Does not exist.

I've had a problem like this before, got advise from this forum, and solved it by comparing the output of bllkid with the contents of /etc/fstab and editing /etc/fstab with the correct uuid.

Now, the output of blkid is:

ubuntu@ubuntu:~$ blkid -c -o
ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ sudo blkid -c -o
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="B69828159827D2A3" TYPE="ntfs"
/dev/sda5: UUID="ddf7a82e-ebca-4dfe-b571-6bb568be614d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: UUID="cb944276-6f8b-4cae-bef6-12d573557e92" TYPE="swap"
/dev/sdb1: LABEL="DRV2_VOL1" UUID="6250A65050A62B2D" TYPE="ntfs"
/dev/sdb5: LABEL="DRV2_VOL2" UUID="28A6-7066" TYPE="vfat"
/dev/sdb6: UUID="e473d790-129c-4f55-926d-0ce11db19c57" SEC_TYPE="ext2" TYPE="ext3"

But /etc/fstab looks like this:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

The last time I ran into this, my /etc/fstab file looked very different and it was obvious what to edit, but this time I'm stuck.

---

### Post by dishbert on 2010-10-13
I just checked the /boot/Grub/menu.lst on the upgraded partition, and it has the correct 10.04 entries.  There is an old Mint version installed on another drive, and the system seems to be booting from that menu.lst, which has the older 8.04 entries.

I think if I could solve the uuid issue the boot loader would find the correct partition and the new menu.lst and all would be well.

---

### Post by dishbert on 2010-10-13
Looking at the upgraded partition, I just rechecked the output of blkid -c -o:

ubuntu@ubuntu:~$ blkid -c -o
ubuntu@ubuntu:~$ sudo blkid -c -o
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B69828159827D2A3" TYPE="ntfs" 
/dev/sda5: UUID="ddf7a82e-ebca-4dfe-b571-6bb568be614d" TYPE="ext3" 
/dev/sda6: UUID="cb944276-6f8b-4cae-bef6-12d573557e92" TYPE="swap" 
/dev/sdb1: LABEL="DRV2_VOL1" UUID="6250A65050A62B2D" TYPE="ntfs" 
/dev/sdb5: LABEL="DRV2_VOL2" UUID="28A6-7066" TYPE="vfat" 
/dev/sdb6: UUID="e473d790-129c-4f55-926d-0ce11db19c57" TYPE="ext3" 
/dev/sdc1: LABEL="FreeAgent Drive" UUID="DAB48589B48568B9" TYPE="ntfs" 
/dev/sdd1: LABEL="Iomega_HDD" UUID="72F44F71F44F369F" TYPE="ntfs" 

And the contents of /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ddf7a82e-ebca-4dfe-b571-6bb568be614d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ce4c935c-cf7d-43bd-9b2b-5b5784b6a460 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/etc/fstab on the old Mint partition looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=e473d790-129c-4f55-926d-0ce11db19c57 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cb944276-6f8b-4cae-bef6-12d573557e92 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I have no idea what's going on here.

---

