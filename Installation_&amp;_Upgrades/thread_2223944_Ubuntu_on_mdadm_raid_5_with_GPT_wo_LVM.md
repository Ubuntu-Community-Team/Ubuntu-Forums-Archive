---
title: "Ubuntu on mdadm raid 5 with GPT w/o LVM"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Mauro_Corti on 2014-05-13
Hello, I am trying to install Ubuntu 14.04 on a desktop with 4*3 TB hard drives in raid 5. The disks are new, therefore empty, and Ubuntu will be the only OS installed.

I am using UEFI boot, I have created a GPT partition table on the drives and using GParted I have partitioned all of them in this way:

1) 250 MB of FAT32, flagged "boot", to be used with mount point /boot/efi
2) 1 GB linux-swap
3) 2.73 TB of EXT4 for the system, to be used with mount point /
4) 100 MB of free and unpartitioned space (I've read on some guides that it's better to live same unpartitioned space at the end)

Using mdadm I have created a raid 5 array between the /dev/sd[ad]3 partitions, but I am not sure how I should behave regarding the boot partition. I've read different stories: some tell I should put them in a raid 5 array, others tell I should just use a raid 1 array, others again claim I should leave them out of the array. What's the truth?

If I should not use an array for the boot partition, do I still need to create one for every HDD? In this case, which one do I flag as bootable?

I've read many guides but none of them talk about raid 5 done on a GPT system with EFI boot :(

As for the swap, I know I do not need to put them in an array, but I don't see the actual harm in doing it: this computer will be used only as a NAS, so there's really not a performance issue here.

Could you shed some light on this issue for me?

Thank you very much!

---

### Post by oldfred on 2014-05-13
Do not know RAID but there are these threads.

 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

I think the solution was to have a grub.cfg in the efi partition pointing to the correct location for the /boot partition.

---

