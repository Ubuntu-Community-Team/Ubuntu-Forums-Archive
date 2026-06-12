---
title: "Lots of confusion on installing for dual boot?"
date: 2017-06-05
forum: Installation &amp; Upgrades
---

### Post by Narfboy93 on 2017-06-05
I've installed Ubuntu for dual boot years ago and decided to revisit it since my company uses Linux and I would like to learn more commands for the system, but this time of installing it is very confusing. I think I am having so much trouble due to how my drives are set up with my computer. Here is what I am working with:

Asus Transformer T200 Tablet/Keyboard dock. 
64Gb eMMC flash storage in the tablet portion that contains the Windows 10 OS.
500 Gb HDD in the keyboard dock that contains my media and other storage. 

I have tried portioning out the 500Gb HDD and having 30 Gb for Ubuntu and 8 Gb for Swap. I originally went through installing the first time with "Along side Windows" and without the swap partition. Then I did the "something else" option and chose the partition for Ubuntu and the partition for the Swap space. For the bootloader I chose the eMMC one time and then the MBR another. All of these ways resulted in the same thing: Booting into Ubuntu gave me a GNU GRUB screen that had a few sentences and the grub>. I tried the ls command and 3/4 listed showed unknown and the other said fat. 

I have also tried installing Mint where this happened as well.

I gather that the bootloader isn't correct? How can I fix this so I can dual boot Ubuntu that is on a separate drive than Windows 10? 

I've also tried clearing all traces of Ubuntu to start "fresh" with my backedup images of my drives but the boot menu still shows two instances of Ubuntu. I tried reinstalling Windows to fix the boot record but it didn't work. So my second point of this post is how can I get rid of these two listing of Ubuntu in my boot menu to go back to factory setting before attempting to install Ubuntu again?

---

### Post by oldfred on 2017-06-05
New systems are the new UEFI/gpt (now 5 years old) not the 35 year old BIOS/MBR.

With UEFI boot loaders get installed to the ESP - efi system partition which is a FAT32 partition with the boot flag.
For whatever reason grub only installs into the ESP on drive seen as sda. Or you have to have an ESP on sda, even if installing to sdb.

And UEFI has NVRAM so it remembers/stores boot entries.
To totally houseclean you have to remove entries from NVRAM and ubuntu folder in the ESP.

If reinstalling you may end up with duplicate entries in NVRAM, but same /EFI/ubuntu folder in ESP will be used/overwritten with new ubuntu/grub.

You can see UEFI boot entries:
sudo efibootmgr -v
You usually have two ubuntu entries. Details will show one as shimx64.efi and one as grubx64.efi. Shim is the UEFI Secure boot version of grub.

If you can install in UEFI boot mode, then run Summary Report from Boot-Repair and post link it gives. Then we can review install.

A lot of this has been fixed, but is your t200 essentially the same as a T100?
 The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)
[http://forums.linuxmint.com/viewtopic.php?f=46&t=140874](http://forums.linuxmint.com/viewtopic.php?f=46&t=140874)

---

### Post by Narfboy93 on 2017-06-05
Thank you, I will look more into the link you shared and fix my boot.

From what I can tell, the T200 is essentially the same as the T100. I'm not 100% familiar with the T100 to say for certain, but it appears to at least be similar enough to have this same issue. That's a bummer that it was the T-series having issues. I will definitely delve more into this issue and the links you mentioned. I have been able to get Ubuntu to load/run off of a Live USB, but that's about it

---

