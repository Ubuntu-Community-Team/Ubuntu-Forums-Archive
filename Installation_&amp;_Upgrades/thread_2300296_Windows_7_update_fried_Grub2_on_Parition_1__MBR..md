---
title: "Windows 7 update fried Grub2 on Parition 1 / MBR."
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by WinEunuchs2Unix on 2015-10-24
Windows 7 did it's usual operating system update while I was watching a movie. When the system rebooted Grub2 scrolled a few thousand lines of bad command / syntax errors and garbage ASCII plus lots of beeps.

I tried boot repair from live CD [http://past.ubuntu.com/12922926](http://past.ubuntu.com/12922926) but it couldn't fix things.

From the GRUB prompt I managed to see that HD0,1 (where Grub parition is) was partially unreadable so I hobbled together linux and initrd.img from HD0,5 (the Linux partition). However after insmod "normal.mod" and running "normal" the same garbage scrolled by with associated beeps.

Now I'm stuck in a terminal screen (tty1) which when logged in just gives me read only access to many files and I'm kind of stumped how to get Windows 7 to reboot and finish the update (which will hopefully restore GRUB and MBR). 

I can't seem to find the chainloader command (to load Windows) and the "set root=(hd0,1)" grub command simply results in "unknown filesystem" error.

I'm also stumped on how I would reformat partition 1 which is only about 100,000 blocks (4,096 block size).

UEFI is turned off.
Secure boot is turned off.
EnhanceIO uses a 12GB partition on an SSD to accelerate 200GB partition of the HDD.

Any clues would be greatly appreciated :)

---

### Post by oldfred on 2015-10-25
You have a BIOS boot install with MBR partitions.

You have NTFS partitions as sda1 & sda2. Your sda1 looks like a typical Windows 7 Boot partition with bootmgr & /Boot/BCD.
But your sda2 has XP boot files, the same boot files as sda1 but no /Windows/System32/winload.exe is shown. Did script just miss it, or was it in some other NTFS partition that does not exist?

Grub is in MBR as it should be and says it will use install in sda5 to boot with.

The space at beginning of drive is not a partition, but used by both Grub & Windows for additional code that users do not normally see. Grub has its core.img in the space after the MBR and before the first partition that now normally starts at sector 2048. With XP first partition started at sector 63.

---

### Post by WinEunuchs2Unix on 2015-11-16
> **oldfred said:**
> You have a BIOS boot install with MBR partitions.

You have NTFS partitions as sda1 & sda2. Your sda1 looks like a typical Windows 7 Boot partition with bootmgr & /Boot/BCD.
But your sda2 has XP boot files, the same boot files as sda1 but no /Windows/System32/winload.exe is shown. Did script just miss it, or was it in some other NTFS partition that does not exist?

Grub is in MBR as it should be and says it will use install in sda5 to boot with.

The space at beginning of drive is not a partition, but used by both Grub & Windows for additional code that users do not normally see. Grub has its core.img in the space after the MBR and before the first partition that now normally starts at sector 2048. With XP first partition started at sector 63.

Hello Fred.

Sorry for the delay... I didn't get an e-mail saying a reply was posted.

The solution.. at the Grub> prompt:

insmod chain
chainloader +1
boot

Then windows starts up. At this point deactivate Intel Rapid Storage Technology (IRST) because foolishly 1 mSata SSD is divided into two partitions to accelerate 1 HDD with a Windows partition and a Linux partition.

Copy as much stuff from sda5 (Linux) to sda2 (Windows) that you can think of /etc /home /boot to rebuild custom stuff later.

Get the gparted & Ubuntu Live CD's to reformat and reinstall from scratch.

There were many steps in between but lets not get into broken dependencies and FSCK finding bad super-blocks.

There are two HDD bays in this Dell Laptop so I should bite the bullet and put another drive in so Windows and Linux are on separate drives. They can both be accelerated on the mSATA SSD (should be upgraded from 32gb) but at least then IRST from Windows won't be stomping all over Linux via BIOS. ie You have to de-accelerate the whole hard drive because Intel deals with the whole hard drive and not a single partition. Linux must be accelerated by EnhanceIO (or something akin) because IRST is Windows only... It's complicated!

I'm surprised this laptop lasted a year before something needed to be reinstalled.

Thanks again for your reply.

---

### Post by WinEunuchs2Unix on 2015-11-26
The thread is marked solved even if cause of the problem is not specifically known.

An install of Windows 10 should be done to make the nag-ware go away but it should be done in a triple boot of Ubuntu, Win 7 & Win 10 via Grub2. Win 10 should be fruitful for xmas gaming season too. Close watch on Vulkan stays in place.

---

