---
title: "Installing from USB"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by billy11 on 2014-03-05
Hello, Im a noob for computer modifications, ive modded my android phone for a couple years and ive been wanting to try modding my laptop now. There isnt much memory on the internal HDD so i was hoping to install 12.04 ubuntu all through my seagate 3tb HDD. 

I tried using "Universal USB installer 1.9.5.2 " to install the iso but as soon as it starts it says it wont be bootable due to an error...

unetbootin does not read my FAT32 partions inside my hdd, or any partitions for that matter. MiniTool parttion wizard and windows file manager both read my partitions, Can someone help me? i know this is an old thread :/

---

### Post by sudodus on 2014-03-06
> **billy11 said:**
> Hello, Im a noob for computer modifications, ive modded my android phone for a couple years and ive been wanting to try modding my laptop now. There isnt much memory on the internal HDD so i was hoping to install 12.04 ubuntu all through my seagate 3tb HDD. 

I tried using "Universal USB installer 1.9.5.2 " to install the iso but as soon as it starts it says it wont be bootable due to an error...

unetbootin does not read my FAT32 partions inside my hdd, or any partitions for that matter. MiniTool parttion wizard and windows file manager both read my partitions, Can someone help me? i know this is an old thread :/

You are welcome to the Ubuntu Forums Billy :-)

I will ask an administrator to create an own thread for you, and to give it a good descriptive title, that should attract people who are interested and have knowledge about your problem. But I suggest that you start by describing your computer:

- brand name and model
- CPU
- RAM (size)
- graphics card/chip
- wifi card/chip

and also what pendrive you have tried (or did you try directly with the USB hard disk?)

---

### Post by howefield on 2014-03-06
Hello billy11,

Your post has been moved to it's own thread, always much better than trying to hijack someone elses as your issue may well be very different. If the thread title needs amending, let me know.

---

### Post by billy11 on 2014-09-24
Sorry for the late response, I got ubuntu 12.04 to work on my 3TB ext hdd eventually, the problem was that i had three different types of formats on the ext hdd and i couldt remember which was which, so a sticky note saved the day! hopefully this helps anyone out, I now have ubunutu on external, windows 8 internal, and kali on a small inside partition (hardest install yet). Now i have a couple questions. 




1. is there a way yet that windows 8 can obey the boot order? (refering to not having to maually enter boot device options everytime) 


2. is ubuntu good for creating android apps? and where would i go to research this and depacking all of the sdk's?

---

### Post by oldfred on 2014-09-24
Post Android questions in a new thread. Not sure what sub-forum perhaps other OS or general?

Is Windows in UEFI or BIOS boot. And is Ubuntu in UEFI or BIOS boot mode?

And what brand, model system? 
Some hard code UEFI to only boot Windows. And Windows 8.1 seems to reset itself as first in boot order. 

Not sure if in UEFI you can set external drive as first and it will keep that first or not?

Some find using efibootmgr works, others still cannot get anything but Windows first.
       Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

      If booted in UEFI mode, you can run this from the terminal:
 modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

