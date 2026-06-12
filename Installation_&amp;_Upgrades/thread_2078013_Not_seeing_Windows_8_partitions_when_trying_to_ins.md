---
title: "Not seeing Windows 8 partitions when trying to install 12.04"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by DugieHowsa on 2012-10-29
Greetings.  I am attempting to perform a Dual Boot installation on an HP P7-1225.

I have already successfully installed Windows 8, and left enough unused space on the drive to install Ubuntu.

When I run the install wizard though, none of the Windows paritions appear (see attached).

I ran the boot repair utility, and it output information here:

[http://paste.ubuntu.com/1316965/](http://paste.ubuntu.com/1316965/)

Any assistance that can be offered would be greatly appreciated.

---

### Post by oldfred on 2012-10-30
Do you have a UEFI system?

You have this message.

GUID Partition Table detected, but does not seem to be used.

Windows when installed in BIOS/MBR mode erases the primary gpt partition table, but one of the advantages of gpt is that is has a backup. Windows ignores backup, but Linux sees both MBR(msdos) and gpt(GUID) so it does not know what to do.

Since you have Windows in MBR, you may just want to delete gpt backup.

First backup partition table
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by DugieHowsa on 2012-10-30
It is an UEFI system.  I believe I initially had GPT partitions installed on this machine with Windows 7 and Ubuntu 12.04.  I wanted to do a fresh Windows 8 install, so I deleted the GPT partition that Windows 7 used, and then also removed the prior Ubuntu 12.04 partition as well.

I will review your suggestions and provide an update once I get home later today.

Thank you.

---

### Post by oldfred on 2012-10-30
Probably would have been better to stay with UEFI, but since that is new we all are learning how to work with that type of install. 
Not sure if Windows 8 would then want you to turn secure boot on. That I would liked to have known. :)
But since you are now MBR, best just to clear backup gpt data.

---

### Post by greg606 on 2012-10-31
I have exactly the same problem. I use Ubuntu 12.10 though.
Please let me know if you succeed.

---

### Post by darkod on 2012-10-31
> **DugieHowsa said:**
> It is an UEFI system.

No it is not. It's one thing the board to have uefi support, it's completely different thing whether you are using it.

I don't know about win8, but win7 only works on uefi with gpt table on the disk, and your disk clearly has msdos table. Hence, it's not uefi boot. Further more, for uefi the first partition on the disk is the EFI System partition and it's FAT32. Yours is NTFS.

Since you already said the disk was gpt earlier, it probably got converted to msdos by windows. In such case windows doesn't delete the backup gpt table and linux can see this and gets confused.

Use fixparts that oldfred mentioned which will remove the backup gpt table. After that you can install your dual boot but it will be in legacy (bios) mode, not uefi.

@greg, if the situation is exactly the same, you can use fixparts too to get rid of the gpt leftovers.

---

### Post by greg606 on 2012-10-31
Yes, I tried it and the installation seems to succeeded. (I'm not sure about this bios stuff at all - maybe it's different on my computer). 
But I have not grub menu - I go straight into windows

---

### Post by darkod on 2012-10-31
> **greg606 said:**
> Yes, I tried it and the installation seems to succeeded. (I'm not sure about this bios stuff at all - maybe it's different on my computer). 
But I have not grub menu - I go straight into windows

Now we are entering another topic so it's better that you open a new thread. Put the basic data in it, including whether you have one disk or more. With multiple disks maybe only the bootloader is on another disk. Try booting from another.

In any case, don't keep replying here, open a new thread. And if you can, it's better to post the bootinfo in your post. You can get the bootinfo with:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

PS. You can also use boot-repair for common boot fixes so you might give the Recommended Repair a go if you want.

---

### Post by DugieHowsa on 2012-10-31
Thanks for the replies everyone.  Originally, my system has efi support, as both Windows 7 and Ubuntu 12 had .efi files on the FAT32 partition, and both appeared as bootable options under system BIOS EFI Boot selector.

I was able to remove the GPT partitions and create MBR partitions, so with regards to that, the issue was resolved.

But what I was ultimately looking for was to have GPT support so that I could have more than the 4 partitions allowed by MBR.

My systems firmware appears to have lost the EFI support, as I can only perform legacy (MBR) functions now.  I am going to work with the PC manufacturer (HP) to see how I can get my hard drive and optical drive to appear again under "UEFI Supported Devices" again in the BIOS.

---

### Post by darkod on 2012-10-31
The msdos partition table (also referred to as MBR) allows only 4 primary partitions, that's true.

But you can also use 3 primary and 1 extended partition which contains many logical partitions. So, it's not impossible to have more than 4 partitions. The only thing is that 3 of them can be primary and the others need to be logical.

Especially ubuntu has no problems working on logical partitions, so you can create them and use them.

---

### Post by DugieHowsa on 2012-11-10
Wanted to finally close the loop on this thread, as I have learned much in the last 2 weeks about UEFI and GPT.

When I initially reformatted my drive, I removed a small 100 MB FAT32 partition that contained the UEFI support for my computer.  Without that partition, I lost all UEFI support, and thus support for GPT partitions, for the computer.  Using the factory restore disks provided by the vendor, I was able to restore the UEFI partition, and this UEFI functionality.

The 2nd problem I was having with the Windows 8 install media I was using.  The ISO I used to create the media did not have UEFI support.  Without UEFI support, the installer could not do anything with the existing GPT partitions.  Thus, it would only allow me to remove all GPT partitions and convert the disk to MBR.

Once I added UEFI support to the ISO, my firmware recognized the DVD as an UEFI supported device, and I was finally able to install both Windows 8 and Ubuntu 12.04 in a dual boot system with UEFI support.

---

