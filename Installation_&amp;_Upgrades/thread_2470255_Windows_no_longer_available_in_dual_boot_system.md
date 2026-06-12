---
title: "Windows no longer available in dual boot system"
date: 2021-12-23
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2021-12-23
I guess my MBR is corrupted as grub no longer appears when I boot.  I know there is a routine I can run to repair this from Ubuntu, but it requires me at one point to insert Windows installation media, which I do not have.  I see online that I can purchase Windows 10 on a stick for a reasonable price.  Will it be possible for me to insert this in lieu of a CD to repair the mbr?

Thanks for any replies.

Caruso

---

### Post by oldfred on 2021-12-23
I believe you can down load the offical Windows installer & run it for 30 days. So then you can use it as a repair disk.
But it is not particularly easy to create a bootable Windows flash drive from Linux. Microsoft has made the .wim file over 4GB, so it does not fit on a FAT32 flash drive. But if UEFI, you have to have UEFI boot in FAT32 ESP partition. Windows tools automatically split the .wim file to make it fit.
Many older instructions on Internet were before the .wim file was over 4GB and now do not work.

If your system is UEFI, and it should be if newer than 2012, then you can directly boot Windows from UEFI boot menu. Often f12 or check your system manual as it varies by vendor.

Always best to have a bootable repair recovery drive for current version of Windows and bootable Ubuntu live installer flash drive to make repairs. And if you update system internally update repair drive also.

Is issue that Ubuntu is not showing Windows boot in menu?
Os-prober now turned off by default Dec 2021
[https://ubuntuforums.org/showthread.php?t=2469993](https://ubuntuforums.org/showthread.php?t=2469993)

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (unless 21.10)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ActionParsnip on 2021-12-24
You can download the ISO for free. You can make a USB stick using another Windows system

---

### Post by howefield on 2021-12-24
> **carusoswi said:**
> ...but it requires me at one point to insert Windows installation media, which I do not have.  I see online that I can purchase Windows 10 on a stick for a reasonable price.

You could use the [Ventoy]("https://www.ventoy.net/en/index.html") utility to create a bootable usb stick to which you can copy most iso files including Windows. 

I don't remember ever needing a Windows installation media to reinstall grub, but it has been so long since I needed it.

---

### Post by carusoswi on 2021-12-30
Thank you for the replies.  After running into a problem that two 256 GB USB flash drives proved to be permanently write protected, I gave up and re-installed Windows 10 Pro also from a flash drive (the OEM CD/DVD drive is not operating).  Prior to the Windows re-install, I backed up all data on my computer to Googledrive.

Windows is working better than ever.  I was surprised to find features that were not available to me from my OEM installation even though I regularly updated it.

Will re-install Ubuntu next to restore my previous dual boot system.

Thanks again, and have a happy New Year.

Caruso

---

