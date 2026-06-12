---
title: "Migrate To New Drive"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by Zim_Zim_Zalabim on 2015-08-16
I have a 500GB SSD drive that I want to clone my 97.7 GB partition over to.  The 97.7 GB partition is part of a 1 TB internal (laptop) drive where the remaining 833.8 GB is a Windows Partition.  The new 500GB SSD drive will be connected to the laptop via USB and is fresh out of the box!!  Can someone give me the easiest simplest steps for someone with little Ubuntu know-how on cloning the 97.7GB partition onto the new larger SSD drive?

---

### Post by howefield on 2015-08-16
What do you mean by "*the remaining 833.8 GB is a Windows Partiton*" - something tells me you don't mean a bootable Windows operating system, or do you ?

Where does Ubuntu fit in this scenario ?

---

### Post by Zim_Zim_Zalabim on 2015-08-16
My 1TB hard drive currently is set to dual boot and is set for 833.3GB Win 7 and the 97.7 GB Ubuntu.  I attempted, obviously very poorly to clone my Ubuntu partition to the 500 GB SSD drive using gparted, and I copied the Ubuntu partition onto the SSD drive and it ran the copy to completion, then i changed the UUID of the SSD Drive and updated grub & fstab then updated the MBR.  However, if I attempt to boot from this drive, it never boots, it sits on the black screen with the blinking cursor?

[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)

---

### Post by Zim_Zim_Zalabim on 2015-08-16
When I plug the SSD drive into my Ubuntu install (dual boot hard drive) and I run ```
sudo fdisk -l
``` This is the results that I show -- does anything here look incorrect?
```

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0ad5b6e9


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *     2048 976773119 976771072 465.8G 83 Linux



```

---

### Post by oldfred on 2015-08-16
Lets see all the details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kurja on 2015-08-17
Can you get to the grub menu when powering up? If you hold down shift when the machine is trying to boot?

I just recently moved my ubuntu install to a new drive and had the same symptom when I brainfarted and tried to boot from the new drive before I had installed grub; I followed [these]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") instructions and it worked. I didn't even need to edit fstab because gparted copied the partitions with their uuids and I wasn't keeping the old drive in the machine.

---

### Post by Zim_Zim_Zalabim on 2015-08-17
Hello @kurja here is the pastebin link with the result, and thank you for the assistance!

[http://paste.ubuntu.com/12109487/](http://paste.ubuntu.com/12109487/)

---

### Post by kurja on 2015-08-17
```
[COLOR=#000000]No boot loader is installed in the MBR of /dev/sda[/COLOR]
```

and

```
[COLOR=#666666]===================[/COLOR][COLOR=#000000] Suggested repair
[/COLOR][COLOR=#000000]The default repair of the Boot-Repair utility would purge [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]in order to fix customized files[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] and reinstall the grub2 of sda1 into the MBR of sda[/COLOR]
```

Try reinstalling grub on sda; I posted a link to instructions above, just make sure you follow them precisely.

---

### Post by Zim_Zim_Zalabim on 2015-08-17
> **kurja said:**
> Try reinstalling grub on sda; I posted a link to instructions above, just make sure you follow them precisely.

Can I do this when it is attached via USB or do I need to connect it as the internal drive in order to do such?  

Forgive my naiveness, does "purge" mean it will wipe the drive or only wipe the MBR?

---

### Post by kurja on 2015-08-17
Default repair offered by boot-repair utility that you posted, would purge and reinstall grub, not any of your files, as far as I can tell (I've never used that utility).

Following the instructions to reinstall grub I linked to, will not remove any of your files.

Whichever way your disk is connected, make sure you have the right sdX when installing grub. You can use gparted, gnome-disks or such to help identify which is which (if you have more than one disk connected).

---

### Post by oldfred on 2015-08-18
The purge is just of grub2. 
Boot-Repair will fix it from the screens you were in when you run the Summary Report.

It looks like you manually installed with just one large / (root) partition. And installed grub2's boot loader to that partition, when BIOS systems only boot from MBR or you must specify a drive like sda as location to install grub2's boot loader.

Often better to have a smaller / and either /home or /mnt/data partition(s).
And some swap is suggested, but if you have 4GB of RAM or more you may not use swap.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Zim_Zim_Zalabim on 2015-08-21
I just ran through the Boot Repair and replaced the Grub 2 bootloader.  Now it boots and sits on a black screen?  I waited on the screen for 20 minutes thinking that any second it will be here.  So now the series of events are as follows, Grub2 bootloder, select Ubuntu then black screen and nothing.  This is the recent scan...

[http://paste.ubuntu.com/12146483/](http://paste.ubuntu.com/12146483/)

---

### Post by ubfan1 on 2015-08-21
Take a look at the first sticky thread in this Installation and UPdates forum ([http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535))
It sounds like you have solved the booting issue and now have a video problem.

---

### Post by oldfred on 2015-08-21
Another Toshiba needed these boot parameters.

 Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

You add like nomodeset, but nomodeset is really only for nVidia or AMD, not Intel.
You may have to hold shift key down until grub menu appears to get menu.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

