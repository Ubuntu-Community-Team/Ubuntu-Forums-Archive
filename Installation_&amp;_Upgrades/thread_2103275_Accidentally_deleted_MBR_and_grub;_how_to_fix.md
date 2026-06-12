---
title: "Accidentally deleted MBR and grub; how to fix?"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by bfootdav on 2013-01-09
Hello all, I think I accidentally deleted the partition on my HD that contained the mbr and grub.  I'm still logged in and was hoping to fix the situation before risking not being able to log in after rebooting.  There are more caveats:

For some reason my computer is refusing as of late to boot with a USB drive even though it did two days ago (when I installed Linux Mint).  I'm not sure if it's a problem with my USB drive or the computer (brand new) but I'm afraid to reboot with the USB drive in case it doesn't work leaving me with a brick.

I am on the road and this is the only computer I have and I'm using whatever free wifi I can find (right now at a coffee house).  It is slow. I'm trying to download Ubuntu and burn it to the USB drive but after 3 hours it's still got several more hours to finish.  Argh.

The grub files do still exist (/boot/grub/grub.cfg) if that helps.

So, I really do not want to take any chances. I need to make sure the problem is what I think it is (deleted the mbr) and to fix it somehow. Please help and thanks.

---

### Post by darkod on 2013-01-09
The MBR is the first sector of the disk and doesn't belong to any partition, so you can't delete it. You can delete the bootloader in it, but not the MBR itself.

Also, unless you have separate /boot partition, then the grub files are inside your main root partition and you can't delete it while running ubuntu because it's running from it.

Are you on windows or ubuntu currently?

Can you post the outputs of these two commands in terminal:
```
df -h
sudo parted -l (that's small L)
```

---

### Post by bfootdav on 2013-01-09
I'm currently in Linux Mint.

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       455G  7.2G  425G   2% /
udev            1.7G   12K  1.7G   1% /dev
tmpfs           684M  984K  683M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.7G     0  1.7G   0% /run/shm
none            100M   16K  100M   1% /run/user

parted -l
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End    Size    File system     Name  Flags
 2      100MB  496GB  496GB   ext4
 3      496GB  500GB  3723MB  linux-swap(v1)

---

### Post by darkod on 2013-01-09
I don't know what was the partition #1, but this looks normal to me. Did you maybe have a small bios_grub partition that got deleted?

I see you have gpt table on the disk and usually with gpt grub2 needs a small partition with the bios_grub flag set. That is on ubuntu, I don't know whether it's the same for Mint.

Can you also post this:
```
sudo parted /dev/sda unit MiB print
```

If there was data you need on /dev/sda1 you can try to recover the partition with testdisk. If it was only a bios_grub partition it's best simply to create new one, and reinstall grub2. No need to restore the exact partition.

---

### Post by bfootdav on 2013-01-09
sudo parted /dev/sda unit MiB print
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 476940MiB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system     Name  Flags
 2      95.4MiB    473390MiB  473294MiB  ext4
 3      473390MiB  476940MiB  3550MiB    linux-swap(v1)


I don't know what was on that small initial partition and that's what has me worried.  

OK, so how would I go about using testdisk or creating a new bios-grub partition? Thanks for all your help on this.

---

### Post by oldfred on 2013-01-09
You should be able to use gparted to create a new bios_grub partition, if testdisk does not find the old one. Most partition tools see a bios_grub as an issue since it is unformatted.

You will not be able to work on the partitions you have mounted with gparted, but should be able to create a partition in the unallocated space. Otherwise you will have to use a liveCD, create partition and reinstall grub from liveCD.

       If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

            You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on


       
 sudo grub-install /dev/sda

---

### Post by bfootdav on 2013-01-09
Thanks everyone, I finally managed to get Ubuntu downloaded (7+ hours) and am installing it now, so the problem is moot.

---

