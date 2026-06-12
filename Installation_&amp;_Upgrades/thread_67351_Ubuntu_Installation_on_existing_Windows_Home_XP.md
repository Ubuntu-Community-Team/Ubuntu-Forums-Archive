---
title: "Ubuntu Installation on existing Windows Home XP"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by elsuirad on 2005-09-20
I have downloaded the zipped file of Ubuntu **Hoary** and **Breezy** and wrote/copied them on separate CD's. **Now my questions are:**

1. How can I start installing either Ubuntu Hoary or Breezy on my existing Windows XP Home Edition? :???: 

2. Are my files will not be erased nor altered after the installation? [-X 

3. If I want to install **ONLY** Ubuntu on a hard disk without **ANY** operating system, **IS IT POSSIBLE? ** :wink: 

4. Will my existing files/programs run again the usual **AFTER** the installation of Ubuntu?

All those who successfully passed on these problems, please help newbies.

Thank you. :grin:

---

### Post by MrCheese on 2005-09-20
[QUOTE=elsuirad]I have downloaded the zipped file of Ubuntu **Hoary** and **Breezy** and wrote/copied them on separate CD's. **Now my questions are:**

1. How can I start installing either Ubuntu Hoary or Breezy on my existing Windows XP Home Edition? :???: 

2. Are my files will not be erased nor altered after the installation? [-X 

3. If I want to install **ONLY** Ubuntu on a hard disk without **ANY** operating system, **IS IT POSSIBLE? ** :wink: 

4. Will my existing files/programs run again the usual **AFTER** the installation of Ubuntu?

All those who successfully passed on these problems, please help newbies.

Thank you. :grin:[/QUOTE]


1 - you need to shrink the Windows partition to give Ubuntu some room. You can either use a Windows (or dos) based program such as Partition Magic, or the linux tools on the Ubuntu cd. Personally I'd recommend you to go for Partition Magic as you are a complete newbie - getting it wrong can be FATAL to your XP system!!

2 - Ubuntu installs in it's own filesystem and does not touch anything else except the boot loader

3 - a blank hard disk is fine - just boot the Ubuntu cd and off you go. If you plan on putting a new hdd in alongside the XP disk you have 2 options - (a) install the bootloader to the XP disk mbr and not mess about with bios boot settings (b) install bootloader to the new hdd mbr and change your bios to boot from the new disk.

4 - the boot loader "grub" will detect your XP system and put it in as an option to boot. You can tinker with grub to set XP as the default o/s if you like once the system is up & running 

One thing to note - the iso files should be burned as disk images not just copied to a cd.

Hope this help :)

---

### Post by elsuirad on 2005-09-20
[QUOTE=MrCheese]
3 - a blank hard disk is fine - just boot the Ubuntu cd and off you go. If you plan on putting a new hdd in alongside the XP disk you have 2 options - (a) install the bootloader to the XP disk mbr and not mess about with bios boot settings (b) install bootloader to the new hdd mbr and change your bios to boot from the new disk.

4 - the boot loader "grub" will detect your XP system and put it in as an option to boot. You can tinker with grub to set XP as the default o/s if you like once the system is up & running 

One thing to note - the iso files should be burned as disk images not just copied to a cd.

Hope this help :)[/QUOTE]

Thanks for a quick response! :wink: 

As for #3: How can I make/create a bootable CD with Ubuntu?
#4 (almost same with #3): boot loader "grub" - where can I find it?

**ISO file vs. zipped file:** The one I have is from the downloaded zipped file, unzipped it on the hard drive then wrote it on CD-R. Do the ISO files are different from the ZIP files? :???:

One thing though, *"(b) install bootloader to the new hdd mbr and change your bios to boot from the new disk."* - is it possible for me to crate a bootable disk (FDD/CD/USB)?

Thanks again! ;-) :-)

---

