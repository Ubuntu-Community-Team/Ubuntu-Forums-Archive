---
title: "GRUB installation errors"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by Baruch on 2012-12-03
I installed Linux Mint and got an error installing GRUB. I ran boot-repair, which also failed and gave me this link: [http://paste2.org/p/2557483]("http://paste2.org/p/2557483")
Can anyone help me with this?

---

### Post by oldfred on 2012-12-03
New drives now are configured to start first partition at sector 2048 for compatibility with new 4K drives or SSDs. It also gives more space from MBR to allow the embedding of grub2's core.img.Your first partition starts at sector 63 which was the standard with XP, Vista changed and then gparted/Linux changed a couple of years ago to start sda1 at 2048.

Something about your core.img, probably the btrfs makes it very large.

Error from Boot-Repair or grub:
> Reinstall the GRUB of sda6 into the MBR of sda
/usr/sbin/grub-bios-setup: warning: your core.img is unusually large.  It won't fit in the embedding area.
/usr/sbin/grub-bios-setup: error: filesystem `btrfs' doesn't support blocklists.
grub-install /dev/sda: exit code of grub-install /dev/sda:1Is there some reason for btrfs?

       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

### Post by YannBuntu on 2012-12-04
[QUOTE=Baruch by email][QUOTE=YannBuntu by email]
You tried to use BTRFS, but your 1st partition (Windows) starts too close from the start of the disk to let GRUB be installed.
I recommend you use EXT4 instead of BTRFS.[/QUOTE]It worked! Thank you!
Where can I find an explanation of why this happens? I am curious.[/QUOTE]

The explanation is that GRUB2 needs a bigger space (before the first partition of the disk) when using BTRFS then EXT4. 
And your disk doesn't have such big space.
You could use GRUB2 with BTRFS if you could increase the free space before your 1st partition.

---

