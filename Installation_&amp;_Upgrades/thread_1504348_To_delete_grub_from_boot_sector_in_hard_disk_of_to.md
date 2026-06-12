---
title: "To delete grub from boot sector in hard disk of toshiba notebook"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by gdvkdd on 2010-06-07
I have a toshiba notebook with Windows Xp and Ubuntu studio. 
I removed Ubuntu partitions with the idea to install classic Ubuntu, but... grub don´t recognize Windows to boot.

I formated the hard disk as slave from another PC. I installed Windows again trying to delete the grub, but, it is already there.

I´m trying to repair grub from Windows with: FIXBOOT, FIXMBR, fdisk /mbr from MS DOS, but that is not working.

So... anybody have suggestions to:

-To delete the hard disk complete and start again everything. (deleting grub also)

or

-To repair boot  sector for Windows

Thanks a lot
gdvkdd
        
                                                                                                                                              [IMG]http://static.forosdelweb.com/images/misc/progress.gif[/IMG]             [[IMG]http://static.forosdelweb.com/fdwtheme/images/buttons/edit.gif[/IMG]]("http://www.forosdelweb.com/editpost.php?do=editpost&p=3433881")

---

### Post by darkod on 2010-06-08
You could have just used the existing partition with Manual Partitioning in the installer, if you happy with the sizes. There was no need to delete them.

If you are doing the XP repair procedure correctly it should work. If it still doesn't, boot with the ubuntu cd in live mode and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

If the hdd is not /dev/sda, use the correct name in the second command. Ignore the warnings it will give.

That will install generic mbr on the /dev/sda disk.

---

### Post by Th3L1zardK1ng on 2010-06-08
> **darkod said:**
> You could have just used the existing partition with Manual Partitioning in the installer, if you happy with the sizes. There was no need to delete them.

If you are doing the XP repair procedure correctly it should work. If it still doesn't, boot with the ubuntu cd in live mode and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

If the hdd is not /dev/sda, use the correct name in the second command. Ignore the warnings it will give.

That will install generic mbr on the /dev/sda disk.

How do you delete grub and wipe both partitions?

---

### Post by darkod on 2010-06-08
> **Th3L1zardK1ng said:**
> How do you delete grub and wipe both partitions?

The commands I posted will write generic mbr on the disk you select, in my example /dev/sda. Another alternative is using windows install cd/dvd which can do the same, install windows bootloader on the mbr.

As for wiping partitions, do you mean formatting them or deleting the whole partition?

Use what ever you want. Gparted from ubuntu (installed, or from live mode), windows Disk Management, etc. There are plenty of options.

---

### Post by dabl on 2010-06-08
If you want to totally delete the partition table and all partitions (and all data) from the hard drive, the "dd" command will do that for you.  Boot a Linux Live CD, get a terminal, and issue:

```
dd if=/dev/zero of=/dev/sdx bs=512 count=1
```

where "x" is the device number for that drive -- probably an "a" unless there are multiple hdds in the computer.

This will render your hard drive "like new", meaning it has no information in the MBR, no partition table, etc. -- it is totally blank.  So, next, you can boot a Parted Magic or GParted Live CD, and use that to make the partitions for Windows, Linux, and swap.  The first question it will ask is the type of partition table you want -- you should choose "MS DOS".  Set the "boot" flag on the first partition, which needs to be large enough for your Windows OS. After the partitions are made, you can boot your Windows installation CD, and install Windows, and following that your Ubuntu CD and install Ubuntu (choose "manual" partitioning, and then just select the partition you already made with GParted).  The last step will install Grub, and it will pick up the Windows OS for the boot menu.

Hope this helps.

---

