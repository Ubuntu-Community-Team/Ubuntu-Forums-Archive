---
title: "Win8 Ubuntu dual-boot failure - Use 2nd disk with MBR?"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2014-05-15
I am trying to install Ubuntu (in this case 13.10 since I made the DVD before 14.04 was ready, next try will be with 14.04) on a friends Lenovo H520 desktop. The goal is to have a dual boot system.

The Lenovo has Win 8 pre-installed and he has no installation disk. It has the full UEFI, secure boot etc. I note that there have been problems with some Lenovo PCs, but I see the H520 is compatible. ([http://www.ubuntu.com/certification/desktop/make/Lenovo/?page=5&category=Desktop&category=Laptop](http://www.ubuntu.com/certification/desktop/make/Lenovo/?page=5&category=Desktop&category=Laptop))

Previous attempts have failed, see [http://ubuntuforums.org/showthread.php?t=2217744](http://ubuntuforums.org/showthread.php?t=2217744)

One key aspect is that the Lenovo has a GPT not an MBR. I assume if I had an MBR, installation would be easier. So how do I safely set up an MBR? 

The easiest would seem to be to get a 2nd hard-disk and install Ubuntu on it with an MBR and boot GRUB from there. Some UEFI questions:

- With UEFI still present, how do I get the system to boot from the 2nd disk?
- Will I still have UEFI problems? 
- Will I get a GRUB offering me a choice between Win 8 and Ubuntu?

Any help appreciated

---

### Post by hans12345 on 2014-05-15
I am trying to install Ubuntu (in this case 13.10 since I made the DVD before 14.04 was ready, next try will be with 14.04) on a friends Lenovo H520 desktop. The goal is to have a dual boot system.

The Lenovo has Win 8 pre-installed and he has no installation disk. It has the full UEFI, secure boot etc. I note that there have been problems with some Lenovo PCs, but I see the H520 is compatible. ([http://www.ubuntu.com/certification/desktop/make/Lenovo/?page=5&category=Desktop&category=Laptop](http://www.ubuntu.com/certification/desktop/make/Lenovo/?page=5&category=Desktop&category=Laptop))

Previous attempts have failed, see [http://ubuntuforums.org/showthread.php?t=2217744](http://ubuntuforums.org/showthread.php?t=2217744)

One key aspect is that the Lenovo has a GPT not an MBR. I assume if I had an MBR, installation would be easier. 

So how do I safely convert the GPT to an MBR, without destroying the Win 8 setup?
(Please note, I have a related question at [http://ubuntuforums.org/showthread.php?t=2224213](http://ubuntuforums.org/showthread.php?t=2224213))

Your help very much appreciated

---

### Post by hans12345 on 2014-05-15
I've been reading OldFred's May 21st 2013 post:

Two Drive installs - See also examples below
Both drives must be gpt partitioned. Best to include efi partition as first partition on every gpt drive, even if booting from Windows efi partition.
Once you are booting with UEFI, best to have all drives and larger external devices even larger flash as gpt partitioned with an efi partition first even if just for future use. May have to manually edit UUID of efi partition, but Boot-Repair updated for two drive installs.
Partitioning
With UEFI, gpt partitioning is required. If multiple drives all bootable drives need to be gpt and best if data drives are also gpt in case later you want to make it bootable. With gpt there is no primary, extended, logical partitions as in MBR(msdos) nor the 4 primary partition limit.
You can only have one efi partition per drive and with gparted you use the boot flag to assign it as the efi partition. No other partitions can have boot flag. Only if booting in BIOS mode with Ubuntu on gpt partitioned drive, you need a bios_grub partition.
Windows will only boot in UEFI mode so you cannot install Windows to gpt drive unless booting with UEFI.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

So it looks like this 2nd disk must be GPT

---

### Post by coffeecat on 2014-05-15
Threads merged. You are asking questions about alternative strategies to deal with the same problem. It only needs one thread.

---

### Post by oldfred on 2014-05-15
Boot-Repair can convert a BIOS install to UEFI if you used gpt partitioning on the second drive and Ubuntu is on second drive. Otherwise from MBR partitioning you can only easily boot with BIOS mode.

UEFI & BIOS are not really compatible, so once you start to boot in one mode you cannot switch. Or if installs are not in same boot mode you can only boot from UEFI menu, not from grub menu.

Even if Ubuntu is on another drive, you need fast boot off in Windows and usually better to have secure boot off. With Windows 8.1 it has been reported that you cannot boot Windows from grub menu with secure boot on. There is a bug report on that.

---

### Post by worleylevi on 2014-05-15
I also have a Lenovo H520 Desktop it had windows 8 but then I formated it to ubuntu but I had the same problem in the bios with UEFI and secure boot. So from my understanding you have 2 hard drives you want to dual boot or just one?

---

### Post by bapoumba on 2014-07-11
Closed as requested here : [http://ubuntuforums.org/showthread.php?t=2233956](http://ubuntuforums.org/showthread.php?t=2233956)
Reopened here : [http://ubuntuforums.org/showthread.php?t=2217744](http://ubuntuforums.org/showthread.php?t=2217744)

---

