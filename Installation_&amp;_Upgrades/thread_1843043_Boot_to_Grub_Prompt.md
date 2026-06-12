---
title: "Boot to Grub Prompt"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by GMallette on 2011-09-12
I hope someone can suggest a solution to my Grub boot problem, on every reboot I get the grub> prompt. I have tried to use all of the examples and suggestions found in these forums but have not resolved the problem so far. I will attach the output from the Boot Rescue CD to explain the details; [http://paste.debian.net/129651](http://paste.debian.net/129651)

I have four 2TB drives setup as a a media server with a small boot partition on sda1 ext4 no RAID, a RAID 1 Swap partition, A RAID 5 ext4 Root partition and a RAID 5 ext4 file store where all my SAMBA shares are stored. I set the boot partition to no raid as I had trouble with setting it up initially in a RAID 1 configuration.

Since the upgrade from 10.04 LTS server to 11.04 server I cannot resolve the boot issue.  There are no other operating systems on the server and I am running the 32 bit version as I initially setup these disks on an old 386 server, now I moved the disks onto a new AMD64 Athlon motherboard and it booted immediatly, until the upgrade. 

I would appreciate anyone's suggestions at this point, generally I work on Windows machines so this is my first serious attempt using Ubuntu and it was working very well for months.

---

### Post by srs5694 on 2011-09-13
Your Boot Info Script output indicates that you're using GUID Partition Table (GPT) partitioning and that you've got Syslinux in your MBR. I'm not sure how it got configured in that way; it's very unusual. Typically, GRUB's MBR code will end up in the MBR. Furthermore, on a GPT disk booting on a BIOS-based computer, you should generally have a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) on the boot disk. (But see below if you're not booting this way.) I don't see any gaps big enough to hold a BIOS Boot Partition, so you'll need to shrink at least one partition to make room for it. In fact, your partitions are not properly aligned for use on Advanced Format disks. You might or might not have such disks, but unless you're 100% positive that they're non-Advanced Format disks, I strongly recommend re-doing your whole partition layout, since [the performance hit for improper alignment can be huge.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) Most new disks of this capacity are Advanced Format models.

If you've got a new computer, it's possible that it's booting in UEFI mode rather than in BIOS mode. This requires an [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) rather than a BIOS Boot Partition. You've got a partition that's marked as such on /dev/sda, but it's got an ext4 filesystem on it, which is improper for an ESP. Thus, I don't think you're currently booting in UEFI mode. If you're not sure if your computer supports UEFI booting, you'll have to post the exact model number of your motherboard or computer, or check the manual (which usually doesn't make the matter quite perfectly clear). FWIW, Ubuntu's installer tends to create dinky ESPs. The usual advice is to make them 100-200 MiB in size, but I prefer making them on the big end of that scale or even bigger -- say, 200-300 MiB. This makes them big enough to hold several Linux kernels, which is useful if you end up using ELILO as the boot loader.

So to sum up, I recommend you do the following:


[list=1]
[*]Wipe all your partitions from all your disks.
[*]Repartition, properly aligning all partitions for Advanced Format use.
[*]When you repartition, create a BIOS Boot Partition of ~1 MiB.
[*]When you repartition, create a FAT32-format ESP of 200-300 MiB.
[*]Re-install everything. If you install in UEFI mode, you'll have to flag the ESP as an "EFI boot partition" (I think that's what the Ubuntu installer calls it).
[/list]

---

### Post by GMallette on 2011-09-13
Hi SRS5694,

I appreciate your help. Syslinux in the mbr came from System Rescue CD, which did not actually help too much in my case. I really need to get samba booted on the original install to recover some files that I did not have storage space to backup before the problem started. Afterwards I will rebuild the entire setup and your input is very useful.   

I do have a new AMD64 Motherboard with 4 Western Digital Hard Drives that are less than 6 months old, so I assume you are correct in your assumptions. I very much appreciate your input, it will make it easier to get it right on the rebuild.

Thanks,

Glenn

---

### Post by srs5694 on 2011-09-13
If you need to get files off the existing installation, there are quite a few options besides Samba. The methods I'm about to specify all begin with booting with an emergency disc such as an Ubuntu installation disc in "try it now" mode or [Parted Magic.](http://partedmagic.com/) These methods include, but are by no means limited to:


[list]
[*]Copying files to a USB flash drive or external hard disk.
[*]Using SSH to transfer the files over the network. This is easiest if you've got another computer with an SSH server installed; you can then use scp from the system on which the files currently reside to do the transfer, as in "scp foo.txt [email]yourusername@server.example.org[/email]:" to copy the file foo.txt to the yourusername account on server.example.org. You can also do recursive copies (to transfer entire directory trees).
[*]Using NFS for a network transfer. This would work much like Samba, but depending on the emergency system, it might be easier to set up than Samba.
[*]Using FTP for a network transfer. There are many FTP servers, some of which are easier to set up than Samba, so this might be preferable in some cases.
[*]Doing local copies on the local disks. For instance, you could do just part of the reconfiguration (involving partitions that don't hold data you need to preserve), copy the data off of other partitions, finish the repartitioning, and move data back to where it belongs. Details would be highly idiosyncratic to your specific setup.
[*]Instead of starting from scratch, you could move/resize partitions so that they're properly aligned. OTOH, such operations are inherently risky, so if you've got valuable data, you really should back it up off the disk before you begin. In other words, this doesn't really solve the problem unless you're willing to risk losing the data.
[/list]

---

### Post by GMallette on 2011-09-16
SRS5694 I have decided to take your advice and I am now rebuilding all the partitions except my large file store. Thanks again for your help.

---

