---
title: "Ubuntu not booting after SUSE installed!"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by DugDra on 2008-07-20
Hi All
I installed SUSE 11.0 on hdb1 and that messed up my Ubuntu 7.10. I ran fsck on the Ubuntu partitions and got it so I can boot 7.10 but only with problems. I looks like fsck is not seeing hda6 and hda7 where I have / and home.  If I type "exit" from the terminal screen Ubuntu seems to load OK.

Something that might be of help. I loaded a live cd and ran a terminal. I could not mount hda6 or hda7.  Dev showed no hda6 or hda7 but did show sda6 and sda7.  I could mount and read sda6 and 7 and Ubuntu and my files seemed to be OK. I'm sure that this was not what I had before loading SUSE. I have print outs of the Partition tables before I made some changes to make space for SUSE. 

7.10 ran OK after the partition changes.

Any Idea what I do to fix this.

Thanks in advance
Doug Drader

---

### Post by tech0007 on 2008-07-20
post the /etc/fstab of 7.10.

---

### Post by DugDra on 2008-07-20
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=442d4da2-2e17-4f10-883b-b4cffe7add0f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=6ea9f88b-e554-4ab0-9e7f-1e33488ac9fb /home           ext3    defaults        0       2
# /dev/hda1
UUID=ACF8F47AF8F4445C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=1D64-1CD6  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda8
UUID=6682-07C4  /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=bafb78e0-94f0-4a79-a90c-bb9a15bec047 /media/hdb1     ext3    defaults        0       2
# /dev/hdb5
UUID=da65b62d-ae8b-42e7-8d24-1b0cd7b84ad3 /media/hdb5     ext3    defaults        0       2
# /dev/hdb6
UUID=4626-EB36  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=a2a65cfd-9551-4de9-876b-c3faada2bae5 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by tech0007 on 2008-07-20
Run 'sudo blkid [device]' to find the UUID of /dev/sda6 and /dev/sda7 and change /etc/fstab accordingly.

---

### Post by DugDra on 2008-07-20
> **tech0007 said:**
> Run 'sudo blkid [device]' to find the UUID of /dev/sda6 and /dev/sda7 and change /etc/fstab accordingly.

blkid.tab after clearing:
<device DEVNO="0x0301" TIME="1216603658" UUID="ACF8F47AF8F4445C" LABEL="WinXP" TYPE="ntfs">/dev/hda1</device>
<device DEVNO="0x0305" TIME="1216603658" LABEL="PROGBACK" UUID="1D64-1CD6" TYPE="vfat">/dev/hda5</device>
<device DEVNO="0x0306" TIME="1216603658" UUID="442d4da2-2e17-4f10-883b-b4cffe7add0f" SEC_TYPE="ext2" TYPE="ext3">/dev/hda6</device>
<device DEVNO="0x0307" TIME="1216603658" UUID="6ea9f88b-e554-4ab0-9e7f-1e33488ac9fb" SEC_TYPE="ext2" TYPE="ext3">/dev/hda7</device>
<device DEVNO="0x0308" TIME="1216603658" LABEL="BACKUP" UUID="6682-07C4" TYPE="vfat">/dev/hda8</device>
<device DEVNO="0x0341" TIME="1216603658" UUID="427f4618-398b-4226-a471-3587f0dc5120" SEC_TYPE="ext2" TYPE="ext3">/dev/hdb1</device>
<device DEVNO="0x0345" TIME="1216603658" UUID="7fbdfdf4-6f1e-4a2b-830f-70becc612370" SEC_TYPE="ext2" TYPE="ext3">/dev/hdb5</device>
<device DEVNO="0x0346" TIME="1216603659" UUID="4626-EB36" TYPE="vfat">/dev/hdb6</device>
<device DEVNO="0x0347" TIME="1216603659" TYPE="swap" UUID="a2a65cfd-9551-4de9-876b-c3faada2bae5">/dev/hdb7</device>

This appears to be what is in fstab.
Any other ideas?

---

### Post by confused57 on 2008-07-20
Maybe I'm looking at it wrong, but hdb1 UUID in fstab and blkid look different.  You could temporarily comment out (#) the hdb1 entry in fstab.

---

### Post by DugDra on 2008-07-21
> **confused57 said:**
> Maybe I'm looking at it wrong, but hdb1 UUID in fstab and blkid look different.  You could temporarily comment out (#) the hdb1 entry in fstab.

I was not looking at those.  UUID for hdb1 and hdb5 are different in fstab.
thanks for seeing this.  I'll copy fstab in the morning and make the changes so if things go more wrong I can get back.

doug drader

---

### Post by confused57 on 2008-07-21
> **DugDra said:**
> I was not looking at those.  UUID for hdb1 and hdb5 are different in fstab.
thanks for seeing this.  I'll copy fstab in the morning and make the changes so if things go more wrong I can get back.

doug drader
I was mainly looking at hdb1, since you installed Suse there, didn't notice hdb5 was different.  From my experience, I believe this will correct your Ubuntu boot problems.

---

### Post by DugDra on 2008-07-29
Thanks confused57 Correcting the UUID for hdb1 and hdb5 in /etc/fstab corrected the problem.

I got busy and just got back to this.

Doug

---

