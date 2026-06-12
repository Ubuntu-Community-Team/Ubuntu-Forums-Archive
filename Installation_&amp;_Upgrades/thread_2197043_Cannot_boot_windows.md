---
title: "Cannot boot windows"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by jauyong on 2014-01-02
Hi, 

I've tried to dual boot with Windows 8.1. I cannot load windows again. There is no option in the GRUB. In what i think is the UEFI boot window i do see options that say windows but it just takes me back to grub.

When I run boot repair I get:

EFI detected. Please Check options
>OK
>Recommended Repair
WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? (if any choice fails, please retry with the other)
>Yes

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6676695/](http://paste.ubuntu.com/6676695/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (1000GB) disk!

The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Please let me know how i can get windows up again and get to dual booting. I've searched the forums and google and no solution has helped me as yet.


Thank you,

---

### Post by fantab on 2014-01-02
```
parted -l:

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  512MB   511MB   fat32                 boot
2      512MB   992GB   991GB   ext4
3      992GB   1000GB  8293MB  linux-swap(v1)

```

Not sure how you did it but you have ERASED Windows partitions. There is no Windows on your computer.

---

### Post by jauyong on 2014-01-02
thanks for the quick reply!

Just to confirm, even though I can see this image below it means windows is gone and I have to reinstall or try to recover with whatever image dell set my laptop up with? 


[IMG]http://i.imgur.com/vkhbKXM.jpg[/IMG]

---

### Post by fantab on 2014-01-02
The above shows just the info about the 'boot loader', the same can also be found on your FAT32 EFI partition. The Windows boot files are still there but Windows is NOT.

---

### Post by oldfred on 2014-01-02
You totally erased drive, so any recovery partition(s) are also gone. If you backed up system or made the recovery set of DVDs then you can restore those, but probably have to remove Ubuntu as Windows will need its partitions and does not see Linux partitions.
If you did not backup before install, you may be able to get the recovery image from your vendor for a nominal charge. That is not the full Windows install, but just the image that you had on your drive that is just an image for your system. 
Or you can purchase a whole new Windows full install.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

