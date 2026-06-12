---
title: "Ubuntu 14.04.1 dual boot win7 efi GA Z68AP-D3 won't boot"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by cryptozoon on 2014-11-24
Folks; I am using a Gigabyte Z68AP-D3 rev 2 with 8GB ram. Two HDDs, both 2TB. 1st drive (sda - an ST2000DM001-9YN164) has win7 64 bit. The 2nd drive, (sdb - an WDC WD20EARX-00AZ6B0) contains an encrypted OS, Ubuntu 14.04.1. The system BIOS was "helpfully" upgraded for me to UEFI, the BIOS version is now Ua5 with a bios date of 06/13/2012 BIOS ID 8A11AG07. There is one more BIOS update available, the Ua9 but I am hesitant to update the BIOS unless I absolutely have to.. There appears not to be any way to shut off secure boot in this BIOS version. I had ubuntu 12.10 dual booting and running alongside win7 just fine, and updated to 14.04. The ubuntu boot menu stopped appearing, and windows boot menu was the only choice. Trying different boot choices in BIOS "ubuntu" "UEFI WDC-WD20EARX" and "SATA pm ST2000DM001" yielded "reboot and select proper boot device or insert boot media in selected boot device & press a key".
  I ran the 14.04 x64 CD as a live disc, and acquired Boot-Repair from repository and ran same. Boot-Repair choked on the task and returned a page, [http://paste.ubuntu.com/8981581/](http://paste.ubuntu.com/8981581/)  . I noticed below line 793 "recommended repair" that operations involving fsck would return "..Warning: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted." I looked at [http://git.kernel.org/cgit/utils/util-linux/util-linux.git/commit/?id=766d5156c43b784700d28d1c1141008b2bf35ed7](http://git.kernel.org/cgit/utils/util-linux/util-linux.git/commit/?id=766d5156c43b784700d28d1c1141008b2bf35ed7) where GPT support seems to have been added, but I suspect the GPT capability was not added into that Boot-Repair. There is also a util at [http://sourceforge.net/projects/gptfdisk/](http://sourceforge.net/projects/gptfdisk/) but I am unsure how to proceed with use of that utility. Paste.ubuntu.etc. may also yield the location of the Grub loader on /sda/ and at the encrypted /sdb/. Using Win7 I can see different efi and grub files using DiskInternals' "Linux Reader" and can see these using Live CD. I suspect the use of a live CD, changing directories and chrooting out of the live CD may yield a success here, but I have not been able to figure out how to do this. I suffered a concussion when a texting Woman ran into my compact car with her Suburban and wrecked my car, my acuity has been lacking a bit for some time now. Please excuse that. Thank You for your time!

---

### Post by cal1j on 2014-11-24
Simple question first of all. Unplug the HDD with Win7 and try rebooting. Does it boot now? If not, what happens. This allows some insight into whether the problem is the dual boot or UEFI. Also, I assume you've gone into bios and switched the UEFI off. If not, try that. Let me know whether either of these are helpful. I have a dual boot Win7 and Ubuntu 14.04 on UEFI (switched off I believe). It was a royal pain, and I spent so much time working around it. Sadly, the process was so lengthy I forget exactly how I did it. Hopefully this is *slightly* helpful

---

### Post by oldfred on 2014-11-25
Best to see details:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is a Microsoft requirement that user be able to turn secure boot off. Some of the motherboard vendors now just call it Windows or "other" operating system. And that is the secure boot setting.
On my Asus I also had to go into CSM mode to turn UEFI on. Seemed backwards but that was how it was configured.

Many Gigabyte boards need iommu settings, either in UEFI/BIOS or as boot parameter or maybe both?

 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by cryptozoon on 2014-11-29
I dropped out the first HDD (/sda/) and rebooted. Got "reboot & select proper boot device or insert boot media in selected boot device & press a key" I also tried a few different combinations to see if grub could be triggered on the second drive (/sdb/) but nothing worked. I contacted Gigabyte and asked how to turn off the "secure boot" ONLY and asked in simple syntax if there was a way to JUST turn off the secure boot. They replied, told me to reflash BIOS backwards into MBR boot mode and offered a way to do this. I replied, that the Ua5 Bios SHOULD have a way to simply turn off secure boot, and would using the Ua9 Bios offer a way to do this? I told them that I didn't want to trade my automobile for a rickshaw but I think the metaphor is lost to them. I await their reply. I think that I DID see some pages from the Ua9 bios which might offer a way to shut secure boot off, but am still checking web sources on that, Thanks!

---

### Post by cryptozoon on 2014-11-29
Thank You, OldFred, I am studying your post!!

---

### Post by oldfred on 2014-11-29
As mentioned on my system Asus AR it was just Windows or "other" operating system.

See if yours is at all similar?
 Screenshots of secure boot settings Asrock, Asus, HP, Acer

[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

Some systems also require you to create password to open up more settings, but never ever lose that password if required.

---

