---
title: "Applied Ubuntu 18.04 updates, rebooted and now receive No bootable device"
date: 2021-02-08
forum: Installation &amp; Upgrades
---

### Post by jimjj on 2021-02-08
I performed an update to Ubuntu 18.04 that required a reboot on Friday.  After rebooting I got the No boot Device message.  I tried boot-repair but it could not fix the issue.  I tried a live USB and fdisk -l shows some "good" partitions, with a boot partition error. and it seems the BIOS setup and some disk recovery tools do not recognize the presence of the hard drive. 

Here's what I get from fdisk -l for the system drive: 

Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           63    786494    786432   384M  c W95 FAT32 (LBA)
/dev/sda2          788480 492577455 491788976 234.5G 83 Linux
/dev/sda3       492578816 493823999   1245184   608M 83 Linux
/dev/sda4       493824000 500118191   6294192     3G  5 Extended


Partition 1 does not start on physical sector boundary.

Hopefully boot-repair posted information to this link:


[http://paste.ubuntu.com/p/4JKHx8P658/](http://paste.ubuntu.com/p/4JKHx8P658/)

---

### Post by Impavidus on 2021-02-09
It says "Paste not Found". Something's wrong with your link.

To solve this, we really need that information on your partitioning and bootloader.

---

### Post by jimjj on 2021-02-10
Edited original post with additional information and new boot-repair report link.

---

### Post by Impavidus on 2021-02-10
This is weird.

There's only partial information on your sda drive. It appears to have 4 partitions. A small fat32 partitions could be an efi partition. Then a large Linux partition, which could be your root partition. Next a small Linux partition, which may be a boot partition or something with recovery tools, as included on some preinstalled systems. Finally an extended partition, which has about the right size for a swap partition, but it contains no logical partitions. Having no boot loader, but a small fat32 partition suggests this is a efi install, but you use mbr partitions, which is a non-standard combination (although Linux allows it).

I don't trust your hard drive. Have you got backups?

Maybe somebody has some brilliant idea on what else could be wrong with your system.

---

### Post by tea for one on 2021-02-10
Yes, weird indeed.

[COLOR="#0000FF"]Line 53[/COLOR] - No OS detected

I would suggest that you boot into a live session and back up your data before anything else.

---

### Post by jimjj on 2021-02-10
OK.  That's all good input.  What I had backed up, also is having issues.  The original installation was from a live CD about a year ago, nothing special.  I am unable to recover many of the files from the larger partition, that I assumed would have been root.  Getting file system errors and partial content.  I was also concerned that the hard drive has issues.  I ran a brief diagnostic that returned no faults, but then parts do not appear to be accessible.  Time to run a thorough check on the drive, and rebuild if possible.

---

