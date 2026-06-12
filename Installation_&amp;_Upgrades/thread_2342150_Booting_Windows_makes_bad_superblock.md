---
title: "Booting Windows makes bad superblock?"
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by furtom on 2016-11-04
I have a Samsung laptop running Win 8.1. I have made sure to turn off fast startup in Windows. It never goes into hibernation, either. The bios is set to secure boot off, and all other sane settings.

Xubuntu installs no problem, efi of course. There&#8217;s a recovery partition sda1, a boot system partition sda2. Some Microsoft mystery partition sda3. Windows proper is on sda4, I have swap on sda5, there are two Samsung recovery partitions, probably have drivers on them or whatever, sda6 and sda7 and Ubuntu install on sda8.

After installation, everything works perfectly. I can boot and reboot into Ubuntu without any problems at all. GRUB efi is booting and working fine. The strangeness begins if I boot Windows. Windows boots fine, but if I boot it just once, it kills Ubuntu completely. The next time I try to boot Ubuntu, boot fails. Initramfs tells me I have a bad superblock. The first time, I ran the whole e2fsck process to fix, which worked sort of... However the problem repeats itself anytime I boot windows, so this is not the solution.

I&#8217;ve reinstalled Ubuntu and even Windows a few times and this has had no effect. I haven't yet gone to third party solutions like EasyBCD, but I may have to try it, though I hate to do that...

---

### Post by fpalmer_35 on 2016-11-06
I have the same problem !

I enter in busybox and have to do a fsck to correct the filesystem.

---

### Post by furtom on 2016-11-06
> **fpalmer_35 said:**
> I have the same problem !

I enter in busybox and have to do a fsck to correct the filesystem.
Right. Then what happens after you boot windows again?

---

### Post by fpalmer_35 on 2016-11-07
If I boot windows (10) no problem, but when I boot Linux again, same error.
I have this problem since I re install ubuntu 16.10 from scratch.
Before it works fine with previous ubuntu release.

Perhaps a problem with the partition size and limits ?

sudo parted /dev/sda unit s print
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       22783999s   22781952s   primary   ntfs            diag
 2      22784000s   22988799s   204800s     primary   ntfs            diag
 3      22988800s   384269912s  361281113s  primary   ntfs            boot
 4      384270334s  625141714s  240871381s  extended
 5      384270336s  384274431s  4096s       logical   linux-swap(v1)
 6      384276480s  625141714s  240865235s  logical   ext4

---

### Post by yancek on 2016-11-07
> There’s a recovery partition sda1, a boot system partition sda2. Some  Microsoft mystery partition sda3. Windows proper is on sda4, I have swap  on sda5, there are two Samsung recovery partitions, probably have  drivers on them or whatever, sda6 and sda7 and Ubuntu install on sda8.

That's not what the output from parted you posted shows.  You have two windows partitions labelled "ntfs diag" which seems a bit odd, not sure?  Your third partition looks to be the largest and is marked as active (boot at the end).  What you indicate is the windows partition (sda4) shows in the parted output as an Extended partition which contains the Ubuntu and swap partitions.   You indicate that you are using EFI so maybe one of the first two partitions is an EFI partition in which case you should have both windows and Ubuntu efi boot files present.  Do you?  If you are using GPT partitioning, both systems should be EFI and from what I understand, windows needs to be EFI with GPT.  If you have GPT, there should be no Extended partitions.

Might be best to get and run the boot repair software from the link below which will show a lot more detail on your systems and boot files and someone more familiar with EFI/GPT might be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by furtom on 2016-11-07
> **yancek said:**
> That's not what the output from parted you posted shows.

My friend, you quoted me, the OP, but I didn't post that! 

Fpalmer_35 said he also had a similar problem and posted his output.

Thank you and cheers,

---

### Post by furtom on 2016-11-07
> **yancek said:**
> That's not what the output from parted you posted shows.

My friend, you quoted me, the OP, but I didn't post that! 

Fpalmer_35 said he also had a similar problem and posted his output.

Thank you and cheers,

---

