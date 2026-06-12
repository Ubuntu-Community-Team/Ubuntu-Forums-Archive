---
title: "Kernel SCSI scan order"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ebursley on 2010-05-02
The Ubuntu Kernel in 10.04 64bit is not scanning SCSI devices in the correct order.

I have two devices that are mirrored disks. 
/proc/scsi/sci shows them as:
Channel: 01 Id: 00 Lun: 00
Channel: 01 Id: 02 Lun: 00

Id: 00 is showing as /dev/sdb
Id: 02 is showing as /dev/sda

This totally messed up my installation yesterday, forcing me to redo a fresh install of Ubuntu 10.04.
Once I figured out the scan order was wrong, I repartitioned accordingly, but then grub installed to the wrong hard drive as well, it defaults to /dev/sda, but since my first LUN is /dev/sdb, I had to boot into rescue mode, and reinstall grub onto /dev/sdb.

My system is now up and running, but even now, the devices are out of order.

Just as an FYI, I used the alternative install CD using a fresh installation.
I've configured the two RAID 1 drives with stripped logical volumes, essentially giving me a RAID 1+0 for the file systems.
/boot is not a logical volume, and resides of /dev/sdb1
/dev/sdb2 and /dev/sda1 are physical disks in my volume group.

The SCSI scan order problem concerns me because if this is corrected in a future release, my system may be unbootable.

---

### Post by cariboo on 2010-05-02
There are two ways to solve the issue, use uuid instead of device labels to mount your drives. to find the blkids at a prompt type:

```
sudo blkid
```

the output should look something like this:

```
sudo blkid
[sudo] password for me: 
/dev/sda1: UUID="98407982-ed69-4691-b483-deecc3b342d1" TYPE="ext4" 
/dev/sda2: UUID="3a7058ef-fd9c-4d72-ad5d-6f169daf24a9" TYPE="swap" 
/dev/sda3: UUID="ffd3b758-e18a-4e1e-b9b3-6d8008a6672a" TYPE="ext4" 
/dev/sdb1: UUID="06170f3a-b780-4ea2-bd4e-c8e4fa07cea4" TYPE="ext4" 
/dev/sdb3: UUID="2ea84cc9-6cc8-4fb6-a16c-f7034c0c1017" TYPE="ext4"
```

The above solution can get a little complicated. For me the easier solution was to set the boot order in the bios. In my bios there is a section to set boot priority, and to set boot order.

---

### Post by ebursley on 2010-05-03
My BIOS for my RAID controller has the order correct. I do have the UUID set in the fstab, along with e2lables and logical volumes, so I'm more confident that my system should boot after a kernel upgrade.

eric@paris:~$ sudo blkid
/dev/sda1: UUID="mWZpcG-ISnA-kiTu-oUST-L7Yo-t2hF-wKhR17" TYPE="LVM2_member"
/dev/sdb1: LABEL="/boot" UUID="a8c77b9f-8e20-4385-acff-4af6185878d4" TYPE="ext3"
/dev/sdb2: UUID="4ty9sj-jiAf-1Cuw-ZLIc-512c-ly31-qmMvgC" TYPE="LVM2_member"
/dev/mapper/vg00-swap: UUID="2192dcd9-94fc-4af6-a812-4558608ecc36" TYPE="swap"
/dev/mapper/vg00-root: LABEL="/" UUID="3fcf76e6-54ab-42b6-8c64-67966c7b97c2" TYPE="ext3"
/dev/mapper/vg00-home: LABEL="/home" UUID="c6b404b8-a582-46e4-83db-7a689abde979" TYPE="ext3"
/dev/mapper/vg00-vm: LABEL="/vm" UUID="c1183747-e9e3-4fe0-8b20-87fa399be419" TYPE="ext3"
/dev/mapper/vg00-var: LABEL="/var" UUID="bb4dc3da-7f06-4165-b84b-713617b012c5" TYPE="ext3"

---

