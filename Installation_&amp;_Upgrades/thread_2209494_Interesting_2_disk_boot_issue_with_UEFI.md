---
title: "Interesting 2 disk boot issue with UEFI"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by smidge on 2014-03-06
Here is the situation. - I have included every detail I can think of to help diagnose the issue.

I have a Lenovo T440s, it came with windows 8.1 pro and all the UEFI stuff that comes with it.

I immediately swapped out the hard drive for an SSD [Samsung 840 EVO], and used the 16Gb Sandisk cache M.2 SSD to install ubuntu. [Installed in the computer initially to cache the HDD]
Booted from a flash drive, installed ubuntu. It worked flawlessly, well at least I thought it did....

While Ubuntu didn't show up in any prompts (no grub during boot) when I held F12 the second drive [Sandisk] showed up, and once i click on it GRUB loads up and i could boot into Ubuntu just fine.

A few weeks back I migrated my data (with Macrium reflect) to a bigger SSD (same model, just bigger capacity) since the one i bought initially just wasn't big enough for windows with all that I need it to do. Everything still works, except now when I hold F12 and go to boot into Ubuntu nothing happens.
Clicking on the SanDisk drive (which hasn't been changed in any way) just returns me to the list of boot devices, the only way out is to choose the primary drive and boot into windows.

A little sad, i persevered and put an Ubuntu ISO onto the very same flash drive (with unetbootin) I used the first time to re-install Ubuntu. [HP 8Gb]
But of course, even the flash drive WILL NOT BOOT all of a sudden!

In a last ditch effort (before bothering the amazing people here at the forums) I disabled secure boot, and enabled legacy mode by default. STILL cannot boot the flash drive or Ubuntu, although I now get a distorted windows 8 logo instead of the Lenovo logo when booting windows 8.1.

What else can I do? I really love Ubuntu and use it more that windows (I am an engineering student with one pc though so i still need windows to work well) 

Thank You for any help you can provide! - post anything you can think of.

I have all the latest updates for everything, newest copy of ubuntu, Windows and bios are all up do date.

---

### Post by oldfred on 2014-03-06
You need to get a flash drive working so you can run Boot-Repair. Perhaps boot loader was over installed or flash otherwise corrupted. May need to make a new one.

Did you install Ubuntu in UEFI boot mode or BIOS boot mode?
Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by smidge on 2014-03-07
Problem was solved by using a different program to re-install ubuntu... unetbootin did not cut it this time. Also making sure that the flashdrive is formatted FAT32 helps.
Ubuntu working with secureboot and everything perfectly again. Thanks for all the help.

---

