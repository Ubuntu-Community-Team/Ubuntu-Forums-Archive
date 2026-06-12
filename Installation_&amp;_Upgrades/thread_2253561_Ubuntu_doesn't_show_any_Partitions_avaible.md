---
title: "Ubuntu doesn't show any Partitions avaible"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by DonMacorli on 2014-11-20
Hello everyone, I am having a problem installing ubuntu. I tried back in January but fail because of the same error...

So I have a hp ultrabook laptop. It came with 4 primary partitions: Recovery, HP_TOOLS, System and C. After searching a little I decided to delete HP_TOOLs and reduce my Windows partition(So i have around 10Gb free). Problem is that whenever I try to install ubuntu it doesn't show anything :/

Does any one now what could I do? Note that after installing ubuntu, i'm planning to reinstall windows since I've had problems with it since last time i tried to install ubuntu(it doesn't reconigze new usb anymore for example)

This is what my computer shows when i type sudo parted -l:

Model: ATA Hitachi HTS72323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1049kB  1016kB  primary
 2      1049kB  210MB   209MB   primary  ntfs         boot
 3      210MB   179GB   179GB   primary  ntfs
 4      179GB   320GB   141GB   primary  ntfs


Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4294MB  4293MB  primary


Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      238kB  2055MB  2055MB  primary  fat32        boot, lba

The last one is my usb where i currently have the ubuntu iso. 

Thanks in advance for any help

---

### Post by irv on 2014-11-20
If you are planning to reinstall windows you need to do this first before installing Ubuntu because if you do it will over write the MBR. It is better to do the windows first. When you reinstall windows do a format.

---

### Post by oldfred on 2014-11-20
Did you create another NTFS partition? You still show 4 primary partitions and with MBR(msdos) that is the limit.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

