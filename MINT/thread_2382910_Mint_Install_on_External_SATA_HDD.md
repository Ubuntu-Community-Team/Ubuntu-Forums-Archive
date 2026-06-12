---
title: "Mint Install on External SATA HDD"
date: 2018-01-18
forum: MINT
---

### Post by mike082013 on 2018-01-18
Hi,

*Here is what I have:*
Lenovo Y500 laptop with internal 480GB SSD containing Windows 10.
New external 250GB SSD (This is **not a USB drive**, but a secondary SATA drive for the Lenovo UltraBay)
Live boot of Linux Mint on a 32GB USB stick.

*Here is what I am trying to do:*
Install Linux Mint onto the secondary drive without modifying the Windows drive. (I would also like to reserve ~100GB for shared storage if possible)

*Here's what I have done:*
Using the live boot I have installed Mint successfully (it seems) onto the secondary drive following basic installation procedures. **However**, when booting the computer I cannot get the BIOS to recognize that the 250GB drive is bootable. I tried Legacy mode and the drive does show up but never can boot. I'm assuming I need to use UEFI mode but I'm not sure why it can't boot from that drive.

What do I need to do to allow the BIOS to recognize the drive as a boot option? I am new to Linux so any advice would be appreciated. Let me know if I can provide any additional info.

Thanks,

Mike

---

### Post by howefield on 2018-01-18
Thread moved to the "*MINT*" forum.

---

### Post by oldfred on 2018-01-19
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If internal drive, just about impossible with Ubuntu (and its similar cousins) to get UEFI grub to install to any drive other than sda and the ESP on sda.
You can create an ESP (FAT32 with boot flag) on gpt partitioned drive and manually copy /EFI/ubuntu from sda to sdb. And reset fstab with new UEFI and create entry in UEFI for booting.
But some computers which I think now include Lenovo's do not like to boot anything other than "Windows Boot Manager" by description. And that requirement is not allowed per UEFI spec.
It should also boot a fallback or hard drive entry, but some only like certain descriptions. It just depends on logic in description checking they use.

Examples of work arounds for description check in link in my signature, if you want to read ahead.

---

