---
title: "Converting USB Installation with Full Drive Encryption from BIOS to UEFI"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by kyle48 on 2015-05-20
This one's a mess, so here goes:

I have a 256GB USB pen drive (/dev/sdd). This drive has three partitions:
/dev/sdd1: a 50GB NTFS partition used for storing files in Windows
/dev/sdd2: a 256MB ext2 partition that is the /boot mount point for the installation
/dev/sdd5: a crypt-luks partition, which maps to /dev/sdd5_crypt (ext4) after entering the password on boot (it's for the full disk encryption)

I followed the instructions [here]("http://www.linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/") on how to set up full disk encryption (FDE) on a drive with multiple partitions (and that's where it specified to create a separate boot partition, unencrypted). The install was successful, and now I can boot from the USB in 'legacy' (BIOS) mode.

The problem is, I didn't realize when I installed it that I don't need to use it on BIOS computers, I need to use it on UEFI computers. So, now I'm trying to figure out how to convert this installation into a UEFI one. There are some instructions on this topic [here]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_mode"), but they don't really seem to be working because a) they don't deal with FDE in those instructions, b) they don't have non-OS partitions to deal with (i.e. my NTFS partition), and c) they don't have a dedicated partition for the /boot mount point to deal with. Now, this is all complicated by the fact that I'm relatively new to this linux bootloader stuff.

Also, do I actually really need a separate /boot partition? I have a feeling it has something to do with the fact that the OS is fully encrypted? Not sure if there's a better way around that.

So my question is, how on earth do I convert this Frankenstein install with so many partitions and with FDE from a BIOS install to a UEFI install? I would really, really prefer not to have to start from scratch because I've done days worth of work in configuring this install. Any help would be greatly appreciated.

Thanks!

---

### Post by oldfred on 2015-05-20
If you are using full drive encryption, you need the separate /boot. And you need an efi partition which can be anywhere from 100MB to 500MB.
But drive must be gpt partitioned to work with UEFI. Did you use MBR or gpt?

You may be able to convert, I have never tried it. And I have only used gpt for all new drives including flash drives since about 10.10.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

      
 Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

Before doing any major changes, make sure you have good backups.

There are some advanced ways to have kernels in efi partition for booting, but I do not know them. You should be able to shrink your NTFS by the amount needed for an efi partition. Efi partitions should be near beginning of drive, but do not have to be first.

---

### Post by kyle48 on 2015-05-20
I'm fairly certain it's MBR. I don't quite understand what you're saying with those two rodsbooks links though, why would I convert to GPT to use UEFI and then use gdisk to convert it back to MBR?

This looks like a mess. Is there a simple way to back up the installation itself so that I can wipe the drive, start over with a new partition table, do everything properly for GPT/UEFI, then restore the OS as I have it now? That might be easier, if it's possible.

---

### Post by ubfan1 on 2015-05-20
On a normal UEFI USB setup, there will be an EFI FAT partition of 200M-500M for the bootloaders.  I think you need the uncrypted /boot, but I'm not sure about that.  You probably have the MSDOS partition table, and contrary to much of what's been written, that will still be fine for your UEFI, Ubuntu boot (consider what the live-media provides if you doubt this).  It looks like you could shrink the NTFS partition (defrag, shrink, chkdsk a few times), and add another partition for the EFI.  If you want to be able to boot on a BIOS computer, your MSDOS partition will make that possible without needing the 1M, unformatted, grub-bios flagged partition.

---

### Post by oldfred on 2015-05-20
I should not have posted the second part on convert from gpt to MBR.

UEFI does work from MBR, but is designed to work with gpt.
Either way with a flash drive, you have to use /EFI/Boot/bootx64.efi as the boot file. You have to copy grub into that folder and rename it to bootx64.efi. And you have to have a grub.cfg to configfile to the actual grub.cfg in your /boot partition.

---

### Post by kyle48 on 2015-05-20
Lots of good answers here, but I'm getting a little lost. Here's what I'm getting out of this:

- I should shrink the NTFS partition by about 500MB, and turn that extra space into a FAT32 partition (I can just do this with Gparted)
- I should somehow make that new partition the EFI partition? This step is what I'm not sure how to do
- I need to create a folder on that new partition, /EFI/Boot/, and then put a copy of grub in it that is renamed?
- I would absolutely love the ability to *also* boot on a BIOS computer, which ubfan1 mentioned, but that requires a new "MSDOS" partition? Or when he says "your MSDOS partition", which partition is he referring to?

I don't mean to be a pain, but this is one of those things where I really need to understand what I'm doing before I start since playing around with it to figure it out will probably destroy my install.

---

### Post by oldfred on 2015-05-20
Partitioning now had two types MBR(msdos) and gpt(GUID).
Then each partition has format and perhaps parameters.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table

      [/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
    
Even if just a NTFS data partition, run chkdsk after you resize from Windows or your Windows repair flash drive.
Generally we suggest using Windows tools for Windows and Linux tools for Linux.

Even if you leave MBR, this has some info:
 Convert MBR drive to gpt and UEFI boot when Windows is UEFI on another drive.
[http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from](http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from)

---

### Post by ubfan1 on 2015-05-20
Sorry, I left out a word -- Your MSDOS partition TABLE leaves enough room for the grub core.img to be stuck in before the first normal partition.  If you had a GPT partition table, there would not be enough room, so in that case, you would need an explicit place for it, typically another 1M partition, no filesystem, flagged with the grub-bios flag.
  To make the FAT partition a recognized EFI partition, flag it bootable with type EF00.
  Putting grubx64.efi into /EFI/Boot/bootx64.efi should work with secure boot disabled.  If you want the boot to work with secure boot either disabled or enabled, put shimx64.efi as the /EFI/Boot/bootx64.efi, and put a copy of grubx64.efi in the /EFI/Boot directory too.  The grub.cfg file remains in /EFI/ubuntu in either case.
  I'd really not recommend trying both BIOS and UEFI bootloaders until you get the necessary UEFI ones working.  Some machines may default to one or the other when both are present, and the default may not be what you need.

---

### Post by sudodus on 2015-05-20
I think it is very difficult and risky to try to convert an encrypted disk to another format. At least you need a complete backup (and verified) if you want to do it.

I would create a new system from scratch (a new installation [in another drive] in another computer). Then I would use ***rsync*** to copy the personal files and settings from the old system to the new system via a local network.

---

### Post by ubfan1 on 2015-05-20
Whatever you do, definitely backup!  Any change to a partition table can potentially go very, very wrong.

---

### Post by kyle48 on 2015-05-20
Ok, I think I'm getting there. I followed the very helpful link that oldfred posted ([http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from](http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from)), so I have added a 200MiB partition flagged EF00 and converted the whole drive to GPT. I'm stuck at the "Install GRUB" step though. In this thread people have said to "Put grubx64.efi into /EFI/Boot/bootx64.efi", "you have to have a grub.cfg to configfile to the actual grub.cfg in your /boot partition", etc. Not being very familiar with GRUB, where do I actually obtain these files? And how do I put them into the partition? Should I mount the partition and drop them directly in there, or mount the partition and create directories inside of it and then put the files inside those subdirectories?

---

### Post by oldfred on 2015-05-20
If you install grub it creates the grub.cfg in the ubuntu folder.
Create a /efi/ubuntu folder.

 In efi partition's folder /EFI/ubuntu add another grub.cfg with configfile entry to tell UEFI where to find grub.cfg with just this one line where example has gpt7 use your partition with the grub.cfg that is the full version or /boot folder or partition.
```
configfile (hd0,gpt7)/boot/grub/grub.cfg
```

Standard version is three lines with a search and default partition. Again add your UUID and partition if you use this:

   ```
search.fs_uuid Your-uuid-here root hd0,gpt8
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

This will show UUID:
sudo blkid

---

### Post by kyle48 on 2015-05-20
So if I'm understanding this right, I should have two files in the EFI partition:

/EFI/ubuntu/bootx64.efi
/EFI/grub.cfg

And the grub file should be as follows:
```
configfile (hd0,gpt7)/boot/grub/grub.cfg
```
What specifically goes in the 'hd0' and 'gpt7' spots? i.e. if my drive is /dev/sdc and the /boot partition is /dev/sdc3, what should I fill in for those spots?

In your earlier posts you mentioned using the /EFI/Boot directory, is that different then the /EFI/ubuntu directory you mention now?

---

### Post by oldfred on 2015-05-20
Internal devices can boot from named folders like ubuntu or Windows. 
External devices use /EFI/Boot/bootx64.efi as default boot. Some internal drives also need this.

So you must copy grub or shim to /EFI/Boot/bootx64.efi.
And grub only reads the grub.cfg as /EFI/ubuntu/grub.cfg

There also are all the support files in /EFI/ubuntu. If copying grub from a standard install, you must copy all those folders into /EFI/ubuntu. It otherwise will complain about missing font and mod files.

If you do a specific install of grub you can specify which of those support files and paths to find them are. But I found it easier just to copy everything from my standard install.

If you change the grub distributor parameter in /etc/default/grub It will install different efi folders. I thought then I found a quick fix to multiple boot. Each of trusty, ubuntu, & vivid has a grub.cfg. This is from my hard drive and does not have to have the bootx64.efi entry.
       /efi/BOOT/bootx64.efi   <--- also is grubx64.efi
/efi/trusty/grubx64.efi
/efi/ubuntu/grubx64.efi 
/efi/vivid/grubx64.efi 

But no matter what you specify to use to boot,  the only grub.cfg that is used is the one in ubuntu folder, not the one in the versioned folder.  It is also somewhere hidden in the config of the grub install to only use /efi/ubuntu. I am still looking, but if anyone knows it would help a lot.

---

### Post by kyle48 on 2015-05-21
Ok, so in the end I gave up with trying to convert it, so I wiped the disk and did a new UEFI installation from scratch. Even with that though, it was having some complications and all your help was invaluable in getting it working (especially with SecureBoot). Thank you all for the excellent help!

---

