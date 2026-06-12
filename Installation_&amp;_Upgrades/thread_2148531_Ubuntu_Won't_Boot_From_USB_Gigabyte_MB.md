---
title: "Ubuntu Won't Boot From USB Gigabyte MB"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by Kodeine on 2013-05-25
So I finally built my first PC yesterday. Now that all the hardware aspects are done I switched to install 13.04 via USB. But it wouldn't list any of my USB devices in the boot menu. I decided to boot the beta of windows eight on my external hard drive which it did happily, displaying the device in the boot menu. I installed the 64bit version of 13.04 on the external drive but it once again won't see it. Then it hit me. UEFI.

One of my hard drives does have an older installation of ubuntu which does boot but I of course want a fresh installation of raring. I read that your supposed to disable quick/fast boot before attempting but there is no such option in the settings. How do I boot ubuntu from USB?

Gigabyte 970a-D3 Motherboard
FX-6300 Six core CPU

---

### Post by grahammechanical on 2013-05-25
I do not understand. What do you mean  by "boot menu?" Do you mean in the Boot system (BIOS/UEFI)? You may find that if Floppy Legacy mode is enabled then you only get a limited set of USB options in the BIOS/UEFI. Disable Floppy Legacy mode and more USB options appear and if you have the USB memory stick pluged in when you enter the BIOS it will show up as a USB hard drive and you can set a boot priority for it.

---

### Post by Kodeine on 2013-05-25
Oops. By the boot menu I mean when you press f12 and it displays the list of devices you can boot from. I went into the BIOS/UEFI and found there was two settings entitled 'Legacy USB' and 'Legacy USB Storage' Disabling them both did nothing as when I rebooted with my external drive plugged in (with the installer for 13.04 64bit), it did not appear as a device able to be booted from when pressing f12.

** So far it's listed my external hard drive to the list of bootable devices when it had the beta of windows eight installed but it never lists any USB stick or external drive when it has had ubuntu 13.04 64bit installed. I just put raring 32bit on one of my USB memory sticks and it again did allow me to boot from it.

---

### Post by ubfan1 on 2013-05-25
Booting an external device under UEFI needs an EFI partition (250M FAT) set up on it.  The removable media boots start out by running /EFI/Boot/bootx64.efi, so if that is a copy of grubx64.efi, it should boot grub, showing the grub menu from /EFI/ubuntu/grub.cfg.  If Secure boot is turned on, then the bootx64.efi needs to be a copy of the shimx64.efi, and grubx64.efi also needs to be in /EFI/Boot.  The 13.04 64 bit install USB will boot 1) legacy mode (has the MBR set up), 2) secure boot mode (has the signed bootx64.efi in its /EFI directory (and the install media is FAT32, so that's OK).  At this point, my knowledge is lacking, what happend on UEFI without secure boot?  It could work if the bootx64.efi is a copy of grub, but it isn't, it's a copy of shim, so maybe you need legacy USB, to allow the MBR style boot.  Do your install media sticks boot on other machines?

---

### Post by Kodeine on 2013-05-26
I've tried them on my off the shelf PC (Lenovo) and they do boot. I've tried my different USB devices with legacy mode en/disabled and to no avail.

**There is an option for CD/DVD booting which allows me to switch between auto, EFI and Non-EFI. Sadly the only DVD drives I have are IDE and my MB only supports sata DVD drives.

---

### Post by ubfan1 on 2013-05-26
Could be a hardware issue.  I have seen the "USB not seen" problem on an HP laptop which periodically overheats and cracks pads on the MCP51 controller, which among other things, controls USB.  I'm on my third motherboard, sigh.  Check the USB options again in the UEFI/BIOS screens, may be something to tweak.

---

### Post by Kodeine on 2013-05-26
I've tried all the different combinations of dis/enabling different settings and using different USB devices with raring and quantal but still to no avail. Look out for a cheap SATA DVD drive in the mean time.

---

### Post by Kodeine on 2013-05-26
Okay I finally found the answer. I'd been trolling through lots of other people who had the same issue and managed to uncover the one person who detailed the fix. I'll share it here so the 'cure' is more abundant.

The partition size of the created USB device needs to be under that of 4GB. I was using a thirty gigabyte hard drive and two eight gigabyte USB sticks. When using the startup disk creator it automatically assumes the entire device with the created partition. I used gparted, after creating the startup USB, and re-sized the partition to 2500mb (actual install size of 13.04 was something like 700mb). Booted up with the USB inserted, went to the boot menu and there she blows.

Note I also tried creating a live USB with another device that was 2GB. This meant I didn't have to re-size the partition as the USB stick could store as much as 4GB. This device did not show as a bootable device however.

So if your having the same issue break out an 8GB USB. Create a live USB, re-size the partition and have fun!

---

### Post by stubright on 2013-06-06
> **Kodeine said:**
> Okay I finally found the answer. I'd been trolling through lots of other people who had the same issue and managed to uncover the one person who detailed the fix. I'll share it here so the 'cure' is more abundant.

The partition size of the created USB device needs to be under that of 4GB. I was using a thirty gigabyte hard drive and two eight gigabyte USB sticks. When using the startup disk creator it automatically assumes the entire device with the created partition. I used gparted, after creating the startup USB, and re-sized the partition to 2500mb (actual install size of 13.04 was something like 700mb). Booted up with the USB inserted, went to the boot menu and there she blows.

Note I also tried creating a live USB with another device that was 2GB. This meant I didn't have to re-size the partition as the USB stick could store as much as 4GB. This device did not show as a bootable device however.

So if your having the same issue break out an 8GB USB. Create a live USB, re-size the partition and have fun!

I didn't use this method or any other methods I found online, I emailed Gigabyte support regarding my problem and they were very helpful. After a few emails back and forth, they sent me a new bios for my motherboard. It now boots correctly with any usb drive I use. 

My motherboard isn't the same as the one from the OP. It's appears to be a common problem with Gigabyte motherboards in general.

So for a proper fix, email Gigabyte. 

Stu

---

### Post by pun2 on 2014-05-10
Apologize for the answer in an old topic.
English is not my native language, i apologize for the illiteracy.

  I am the owner of Gigabyte GA-965P-S3 BIOS F14. For various reasons, the only possible installation method is to install from the thumb drive. Faced with the problem as the author of this topic. Thumb drive with ubuntu is not determined by the BIOS and is not added to the boot menu (F12 -> Hard disk). Thumb drive recorded with UltraISO Windows7 normally determined and it is possible to boot. At the same time thumb drive with ubuntu properly loaded laptop and virtual machine (via plpbt). As previously mentioned, the BIOS first checks if all the thumb drive and arranges then adds it to the boot menu (if the thumb drive does not meet the requirements then it is does not added to the boot menu). Googling a bit and thinking about this problem found a solution for my situation.

    The figure below shows an [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of thumb drive with Win7 created using UltraISO. Thumb drive is determined normally and it is possible to boot from. I draw your attention to the fact that information about the partition is written in the **entry #4**.
[IMG]http://spuncher.front.ru/img/Ubuntu/thumb_Win7.png[/IMG]

The figure below shows an MBR of thumb drive with ubuntu created using UniversalUSBInstaller. Thumb drive is **NOT** determined and it is **NOT** possible to boot from on my motherboard. While on the other computers it is possible to boot from. I draw your attention to the fact that information about the partition is written in the **entry #1**.
[IMG]http://spuncher.front.ru/img/Ubuntu/thumb_ubudntwork.png[/IMG]

The figure below shows an MBR of thumb drive with ubuntu created using UniversalUSBInstaller and **swapped partition entry #1 and entry #4** (via HEX-editor). Thumb drive is determined normally and it is possible to boot from on my motherboard. Other computers boot is also possible. I draw your attention to the fact that information about the partition is written in the **entry #4** (partition entry #1 and entry #4 swapped).
[IMG]http://spuncher.front.ru/img/Ubuntu/thumb_ubuwork.png[/IMG]

It seems the problem is caused by the fact that BIOS incorrectly interprets MBR partition entry. Other vendor does BIOS more flexible.

P.S.
Before using UniversalUSBInstaller i prepared thumb drive by executing this commands
DISKPART> list disk
DISKPART> select disk 2 (insert your flash number listed above)
DISKPART> clean
DISKPART> create partition primary
DISKPART> format fs=fat32 quick

---

### Post by pun2 on 2014-05-10
add 
Thumb drive - transcend jet flash v20 8GB.
Size is not trimmed. One partition takes up the whole space.

---

### Post by Matthew_Pollock on 2014-10-09
This was Gigabyte's reply to me - they don't support Ubuntu

Dear Customer, 

The latest BIOS for this board is F5.

You are trying to use Linux OS USB drive on our motherboard. We don&#8217;t guaranty Linux OS on our motherboard due to it&#8217;s a open source software. Thanks.

---

### Post by oldfred on 2014-10-09
That seems to be their standard reply, and many vendors do not want to devote resources to anything but Windows.
But many users have found work arounds and install Linux to just about every system.

Gigabyte also has iommu issues and settings or parameters are required.

---

