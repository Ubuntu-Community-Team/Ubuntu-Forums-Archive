---
title: "Fix bootloader for Windows 10 and LVM encrypted Kubuntu on different disks"
date: 2019-07-30
forum: Installation &amp; Upgrades
---

### Post by EkViLiBRiUmM on 2019-07-30
Hello good people of Ubuntu Forums!

1st post ever, this forum has saved my ass more times than I can remember :KS

I have W10 freshly installed on one disk. After that I installed Kubuntu 19.04 and chose to encrypt the whole disk.
Since then, I can only see Kubuntu entries in the *Choose boot device* section when computer boots up.

I was gonna follow [these instructions]("https://windowsforum.com/threads/reinstalling-bootloader-on-a-different-disk.242258/post-723473"), but I'm not being able to boot into W10 installation media.

Maybe I messed up the Windows USB while creating it in Kubuntu.

Used several methods for this:
(1) Created NTFS partition with Gparted and then copied .iso contents into the USB manually
(2) Used WoeUSB

Either way, it's not recognized as a bootable installation media.

Windows is installed in /dev/sdb
Kubuntu is installed in /dev/sde

This is my fdisk -l, if it helps:

```
&#10140; sudo fdisk -l
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: MKNSSDRE1TB     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A8522167-1C10-4880-8238-3ABC2D00C2B8


Device      Start        End    Sectors   Size Type
/dev/sda1      34     262177     262144   128M Microsoft reserved
/dev/sda2  264192 1953523711 1953259520 931,4G Microsoft basic data




Disk /dev/sdb: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 745FB2E5-EDEF-4C16-99C5-9D1F1C611C4E


Device     Start       End   Sectors   Size Type
/dev/sdb1   2048     34815     32768    16M Microsoft reserved
/dev/sdb2  34816 488396799 488361984 232,9G Microsoft basic data




Disk /dev/sdc: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: SAMSUNG HD103UJ 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 07E4583A-70DA-41C7-93E8-6A6C8C617BF6


Device     Start        End    Sectors   Size Type
/dev/sdc1   2048 1953523711 1953521664 931,5G Linux filesystem




Disk /dev/sdd: 3,7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: HGST HDN726040AL
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7D839F78-9281-450A-A00E-AC9AFCC77BEB


Device      Start        End    Sectors  Size Type
/dev/sdd1      34     262177     262144  128M Microsoft reserved
/dev/sdd2  264192 7814035455 7813771264  3,7T Microsoft basic data


Partition 1 does not start on physical sector boundary.




Disk /dev/sde: 447,1 GiB, 480113590272 bytes, 937721856 sectors
Disk model: WDC WDS480G2G0A-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2AA4B028-427F-4AF3-8559-0FAB4CF3C99D


Device       Start       End   Sectors   Size Type
/dev/sde1     2048   1050623   1048576   512M EFI System
/dev/sde2  1050624   2549759   1499136   732M Linux filesystem
/dev/sde3  2549760 937719807 935170048 445,9G Linux filesystem




Disk /dev/mapper/sde3_crypt: 445,9 GiB, 478790287360 bytes, 935137280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/kubuntu--vg-root: 445 GiB, 477760585728 bytes, 933126144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/kubuntu--vg-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

Any help is much much appreciated :)

---

### Post by cruzer001 on 2019-07-30
Since it all fresh I would start over again, reload windows, set aside a partition using windows part manager for kubuntu, then install K.

I don't full disk encrypt, I just incrypt a directory in my home folder, keeps it simple for me.  What about EFI, could that be a problem?

[https://ubuntuforums.org/showthread.php?t=2423791&p=13876324#post13876324](https://ubuntuforums.org/showthread.php?t=2423791&p=13876324#post13876324)

There are of course other repair routes to take, have to see who else chines in :)

---

### Post by oldfred on 2019-07-30
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
 Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

It looks like you used Windows tools to partition drives as each has the Microsoft reserved partition as first. Windows does that as its standard.
I am also not seeing the typical Windows UEFI/gpt partitions:
       
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by EkViLiBRiUmM on 2019-07-30
> **cruzer001 said:**
> Since it all fresh I would start over again, reload windows, set aside a partition using windows part manager for kubuntu, then install K.

I don't full disk encrypt, I just incrypt a directory in my home folder, keeps it simple for me.  What about EFI, could that be a problem?

[https://ubuntuforums.org/showthread.php?t=2423791&p=13876324#post13876324](https://ubuntuforums.org/showthread.php?t=2423791&p=13876324#post13876324)

There are of course other repair routes to take, have to see who else chines in :)

Hey!

I really don't want to start over with the Ubuntu disk because it's my work environment and the setup is already working (which is long and painful to do from scratch).

I don't have a problem starting over with W10 disk, but I think you misunderstood my situation. I have each system in a separate physical disk.

And regarding encryption, I do need to have the whole disk encrypted for security reasons related to my job (stolen computer, for example).

---

### Post by EkViLiBRiUmM on 2019-07-30
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
 Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

It looks like you used Windows tools to partition drives as each has the Microsoft reserved partition as first. Windows does that as its standard.
I am also not seeing the typical Windows UEFI/gpt partitions:
       
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

The thing with the UEFI/GPT partitions missing is a mistery to me. I did remove every partition from the Windows disk when setting up the installation, and it prompted saying that Windows was gonna create a few extra partitions for me (which I thought was referring to these missing partitions we're talking about).

Thanks for your reply. I will post the boot-repair summary report later today while on live Kubuntu.

---

### Post by EkViLiBRiUmM on 2019-07-30
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
 Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

It looks like you used Windows tools to partition drives as each has the Microsoft reserved partition as first. Windows does that as its standard.
I am also not seeing the typical Windows UEFI/gpt partitions:
       
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Here's the report using boot-repair with working Kubuntu install: [http://paste.ubuntu.com/p/dtw4H6NqY3/](http://paste.ubuntu.com/p/dtw4H6NqY3/) :KS

---

### Post by oldfred on 2019-07-30
You show no Windows boot entry in UEFI.
Your Microsoft reserved partition, which Microsoft creates when making gpt partition on sda, is much larger than typical reserved partitions. And is similar in size to a BIOS/MBR Windows boot partition.
So did sda get converted from MBR to gpt, erasing the Windows boot partition and the Windows BIOS boot files in it? Since Microsoft reserved is unformatted. You may be able to convert back to MBR and convert (not reformat) sda1 to NTFS with boot flag & Microsoft boot files may reappear?

Since UEFI system probably better to reinstall Windows in UEFI boot mode. Not particularly easy to convert BIOS Windows to UEFI Windows, but did see somewhere info that it can be done.

Not sure why Boot-Repair wants to reinstall grub in BIOS mode on gpt drive. That is why it wants a bios_grub partition. Did you decrypted your install before running Boot-Repair? It need to see fstab inside your encrypted partition to know you have ESP mounted, so then UEFI install.

---

### Post by EkViLiBRiUmM on 2019-07-31
Hello!

For history purposes I will post my solution here.
I ended up burning the W10 iso with WoeUSB under my working Kubuntu installation.
Before rebooting, I deleted the Microsoft Reserved Partition on the disks that didn't have any meaning to have it there:

/dev/sda1
/dev/sdd1

Used Gparted for this. Left deleted space as unallocated on both disks.

Then rebooted and selected as boot device my USB with the freshly burnt Windows iso, and followed the instructions [here]("https://windowsforum.com/threads/reinstalling-bootloader-on-a-different-disk.242258/post-723473")

Everything went smoothly :)

Used 500 MB for the shrinking / new boot partition on Windows disk.

Thank you both @oldfred and @cruzer001 for your help

---

