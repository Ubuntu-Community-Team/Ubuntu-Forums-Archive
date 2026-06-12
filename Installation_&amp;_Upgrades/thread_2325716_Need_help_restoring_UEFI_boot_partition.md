---
title: "Need help restoring UEFI boot partition"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by zefreak on 2016-05-24
(I posted this in the beginners forum but feel like this may be the place for it, let me know if I should delete one or the other)

Hi everyone,

I've only been using Ubuntu for development for a few months, and am still learning my way around.

Last night I accidentally formatted my boot partition. I had windows 10 and ubuntu installed using grub bootloader. The drive is ptk (i believe).

I am getting an error when running boot-repair about gpt drive and needing to create a partition with a boot flag, but I've seen various (old) comments online about how this is the wrong thing to do.

I have the info dump on pastebin if anyone would like to help.. I don't  have the windows cd anymore and there is a lot of important data on the  disk so I would love to get this working again.
[URL="http://paste.ubuntu.com/16660200"]
paste.ubuntu.com/16660200[/URL]

Thanks

---

### Post by watchpocket on 2016-05-24
You should delete the other one.  I did that once, and one of the forum moderators deleted the one in the forum I wanted it in, and left it in the forum I didn't want it in.  (Sorry I can't help with your actual problem but good luck.)

---

### Post by yancek on 2016-05-24
The link below has an explanation of how to resolve this problem if you have the windows recovery CD you created when you first booted windows.  I don't know what it will do to your Ubuntu entry in the EFI partition.  The method below is for repairing an EFI partition though and it is not clear to me that is what you deleted or if you had a separate boot partition for windows??

 [http://blog.d0zingcat.xyz/2015/09/28/Windows/How%20to%20repair%20the%20EFI%20Bootloader%20in%20Windows%2010/](http://blog.d0zingcat.xyz/2015/09/28/Windows/How%20to%20repair%20the%20EFI%20Bootloader%20in%20Windows%2010/)

> I am getting an error when running boot-repair about gpt drive and needing to create a partition with a boot flag

That sounds like creating a BIOS boot partition unformatted to use GPT without UEFI.  That won't work with windows as it needs UEFI with GPT.  You might clarify or post a link to the boot repair output.

---

### Post by zefreak on 2016-05-24
Thanks for the reply,

Here's the link to the output - [paste.ubuntu.com/16660200]("http://paste.ubuntu.com/16660200") 

The drive is formatted GPT and I was using UEFI with safe boot disabled

---

### Post by LostFarmer on 2016-05-24
> Last night I accidentally formatted my boot partition.  Do not know if you formatted the partition but you did delete the partition.  If all you did was delete the partition you need to run in a terminal 'testdisk' to recover the partition, the data will still be there.  do a goggle on how to use testdisk..  That will be mush easier then rebuilding the MS EFI needed files, you would need a MS repair cd/usb.  I would suggest once you get back running , make a recovery/repair cd/usb.

---

### Post by zefreak on 2016-05-24
> **LostFarmer said:**
> Do not know if you formatted the partition but you did delete the partition.  If all you did was delete the partition you need to run in a terminal 'testdisk' to recover the partition, the data will still be there.  do a goggle on how to use testdisk..  That will be mush easier then rebuilding the MS EFI needed files, you would need a MS repair cd/usb.  I would suggest once you get back running , make a recovery/repair cd/usb.

Thanks for the response, I'm looking into the tool now. I think you are correct that it is deleted but probably salvageable

---

### Post by oldfred on 2016-05-25
It looks like you deleted 3 partitions, probably a Windows restore, the ESP - efi system partition & Windows System Reserved. 
You need the ESP to boot in UEFI mode and Windows really prefers to have the System Reserved, but that is more for some special software which is not normally installed.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

Windows typically uses 100MB for the ESP  - FAT32 with boot flag and 128MB unformatted for System Reserved.

Boot-Repair can totally uninstall and reinstall grub in either UEFI or BIOS boot mode or convert from one to the other.
But you have to have an ESP for UEFI boot or a bios_grub for BIOS boot, and Boot-Repair does not create partitions. You have to use gparted.

And since Windows is UEFI, you really want Ubuntu in UEFI boot mode.
Once ESP is created, Boot-Repair can reinstall grub and get Ubuntu working. But it cannot fix Windows.
You will need a Windows repair flash drive or installer with repair console to fix Windows. That will add back the /EFI/Microsoft folder in the ESP.

You may be able to fully restore partitions with testdisk or find the missing files.
It just is testdisk will not find the System Reserved and may make a partition a 128MB too big. It normally is 128MB just before the first NTFS partition in gpt partitioned drives.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 

     [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    
If you know sizes of missing partitions, you can also use parted rescue.

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by zefreak on 2016-05-25
Thank you so much LostFarmer and oldfred, great information. I was able to use testdisk to restore the efi partition (and windows restore, you were correct). I can now boot into ubuntu, which is primarily what I need.

I will leave restoring windows boot for a later date, and set this to closed

---

