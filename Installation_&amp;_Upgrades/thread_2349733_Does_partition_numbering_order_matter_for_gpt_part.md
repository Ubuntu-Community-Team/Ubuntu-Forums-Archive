---
title: "Does partition numbering order matter for gpt partitions"
date: 2017-01-17
forum: Installation &amp; Upgrades
---

### Post by efflandt on 2017-01-17
I know that many people who had issues in the past seemed to have msdos partitions in a mixed up order (not in numerical order), but I do not know if that was a cause of issues they were having. That hasn't been a problem for me before because usually Windows utility or recovery partitions are before Windows, and I can simply shrink Windows (or replace existing D: data) partition to install Linux.

But I have not worked with gpt partitions or UEFI before and this HP Win10 laptop has 2 partitions after the point where I would shrink Windows and add Ubuntu. So would gpt partitions not in numerical order (like 1,2,3,6,7,4,5) be a possible issue for anything?```
ubuntu@ubuntu:~$ sudo parted -l /dev/sda
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB   978GB   978GB   ntfs         Basic data partition          msftdata
 4      978GB   979GB   882MB   ntfs                                       hidden, diag
 5      979GB   1000GB  20.9GB  ntfs         Basic data partition          hidden, msftdata
```Also does install automatically take care of whatever is required to be altered/added to the EFI boot partition? Output of gparted attached.

The laptop is a low end HP with Pentium quad-core with touch screen that I bought to set up for a retired person who then decided they could not afford it at this time. It only has a single RAM slot upped from 4 GB to 8 GB. I have only been using it for WebEx which works somewhat better in Windows than 32-bit only Linux WebEx in a 32-bit virtualbox. It works fine for that and has long battery life, but is too slow for any gaming.

I am not new to Linux, I have been using it for over 20 years, since before Windows had native dial up networking or a web browser. I am just new to UEFI and gpt partitions.

---

### Post by igdfpm on 2017-01-18
The order of partitions makes no difference at all.

If you wish to retain the factory recovery mode for Windows then it would be advisable to shrink the C: partition and leave all other partitions in place - placing the linux install in between the existing layout.

In your gparted screenshot you would shrink sda3 (I have very little use for W10 so only give it 120GB - your choice) and then manually precreate your linux partition(s) in the freespace between sda3 and sda4.

Whether you install linux to one partition (sda6 ) or with a separate home (sda6, sda7) is entirely up to you (other schema are available) although I would suggest setting them up in gparted in advance as I find the installer partitioner kinda clunky and don't want to leave anything to chance. This can all be accomplished from the "manual" or "something else" option at install time.
 
The installer will "auto detect" the existing EFI partition and install efi grub for you - I always double/triple check that the EFI partition (sda1) is **NOT** flagged to be formatted as this would destroy your existing Windows efi entry and would be a very bad thing to do ;)

Good luck :D

---

### Post by sudodus on 2017-01-18
> **igdfpm said:**
> The order of partitions makes no difference at all.


+1

Example:

I create persistent live drives with a usbdata partition with NTFS as partition #1 located at the end of the drive. At least old versions of Windows 'see' only partition #1 on USB drives.

So the partition numbers need not match the location on the drive. See this link: [mkusb/persistent#Partitions](https://help.ubuntu.com/community/mkusb/persistent#Partitions)

---

### Post by oldfred on 2017-01-18
What model HP, they typically are not UEFI dual boot friendly.
They specifically violate UEFI spec that says NOT to use description as part of UEFI boot.
And of course only valid description is "Windows Boot Manager".

If only booting Ubuntu, you can just change the ubuntu entry to read "Windows Boot Manager". They just check description.

If dual booting, UEFI has a fallback or hard drive boot entry that usually works. That requires copying some files and perhaps adding the fallback entry into UEFI.
Boot-Repair now does the file copy to /EFI/Boot/bootx64.efi which is the fallback boot entry in the ESP - efi system partition. You just need to use Boot-Repair's advanced mode and check the "use the standard efi file".

More details in link in my signature.

Before Boot-Repair copied files, users manually copied them.
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by efflandt on 2017-01-18
It is a relatively new HP Notebook 15-ac147ds sold by HSN (Home Shopping Network) late last year with Win10 and touch screen. I disabled fast boot and thought I disabled secure boot in UEFI. But when I read that secure boot should not be a problem anymore and checked its setting, it was still enabled, and I had no trouble booting a live system from USB memory stick. I am used to using a mouse instead of touch screen, but just tried that and the touch screen works in Ubuntu.

I'll image its hard drive before tampering with it, but if all else fails, I don't have anything important on it and did create its recovery system on bootable USB stick. Thanks.

---

### Post by yancek on 2017-01-18
If you are new to UEFI, you might want to take a look at the Ubuntu documentation at the link below before starting.  Should clear up a number of questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by efflandt on 2017-01-20
Thanks, it went easier than I thought. I used Win10 to shrink its partition, used Other during install to create swap and / partitions. And it booted right into the grub menu. But swap was just a little too small since the dialog for creating partitions uses GiB instead of GB, and after I fixed that with gparted on live/install USB, it booted into Win10 instead of grub menu. I tried to shift ubuntu before Microsoft in UEFI/BIOS settings, but it still booted right into Windows. I guess that is good for stealth Linux, I just have to tap Esc per second while booting, F9, then select ubuntu.

---

