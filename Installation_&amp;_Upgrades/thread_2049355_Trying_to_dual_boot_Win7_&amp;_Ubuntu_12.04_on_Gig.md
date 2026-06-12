---
title: "Trying to dual boot Win7 &amp; Ubuntu 12.04 on Gigabyte H77 -  boots straight to Windows"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by ambient007 on 2012-08-28
Goal: to dual boot Windows 7 and Ubuntu 12.04 (both 64-bit) from a single hard-drive with a [Gigabyte ga-h77m-d3h]("http://www.gigabyte.us/products/product-page.aspx?pid=4143#ov") Motherboard.

Problem: After installing Windows 7 and then Ubuntu from USB without error,  the machine boots straight back to Windows - not showing any boot-loader. 

The Ubuntu live USB continues to work.

I have tried wiping and installing a number of ways: the automatic 'install alongside windows' option as well as specifying the partitions manually.

Using EasyBCD did not work for me.



Perhaps is could be something to do with my 'BIOS'? The mobo came with '3D Bios - Dual UEFI'; I don't pretend to know much about UEFI but I've read that it can cause some issues when dual booting.

When I look at the boot order with the liveUSB inserted, there is a UEFI label with the device.




I don't know what to try next. There isn't any data on the computer, just the operating systems so I don't mind reinstalling (again) if I have to.


Any and all help is much appreciated!!

---

### Post by darkod on 2012-08-28
Yes, UEFI makes big difference.

For UEFI you need to install ubuntu in uefi mode too, in other words, boot the usb stick in uefi, not the standard mode. You said in the boot menu there is uefi label with the device, use that.

For windows or ubuntu to be installed in uefi they need to be booted in uefi mode.

I'm not sure if that's enough for it to work, because there are other issues with uefi too, but that's a start.

---

### Post by ambient007 on 2012-08-28
Thanks for your reply!

When I said there's a UEFI label above the usb stick in the BIOS boot order menu, I meant that  I can't see any alternative.
The only thing that shows up is that and my harddrive.

I'll delete the current Ubuntu partitions and try and see if I can boot it in some other way I guess?

Would I need to do the Windows side as well or would that've installed in UEFI mode automatically?

Could the way the startup USB is created somehow affects if it boots in UEFI mode or not?


Sorry, I don't understand this stuff too well.

---

### Post by darkod on 2012-08-28
The cd you can boot in both modes, about usb I'm not sure if it depends how it was created. I don't use uefi and don't have many details except few things mentioned here on the forum.

Windows should have installed in uefi automatically if uefi is enabled on the board. You can test also if you boot the ubuntu usb in live mode (doesn't matter uefi or not), and in terminal execute:
[code]sudo parted -l[/code+

If it says the partition table on the hdd is GPT, then windows is in UEFI because it can only work with gpt on uefi. Otherwise, it works with msdos table in the standard bios boot mode.

---

### Post by drmrgd on 2012-08-28
You actually might be OK with the way you've set up.  In my ASUS UEFI BIOS, there is an option to boot the USB device either in BIOS mode or UEFI mode.  Perhaps you don't get that option in your BIOS and boot into UEFI by default?

The best thing to do would be to run the "Create Bootinfo Summary" portion of the Boot Repair package:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

With that we can have a look to see how Windows is setup and what the boot partition looks like.  It might be a simple matter of configuring Grub to pick up the slack.  Please post the results of the Bootinfo Summary here with code tags and we'll see if you need to reinstall or if you're already OK.

---

### Post by ambient007 on 2012-08-28
Well I just reinstalled Ubuntu again after confirming the USB was booting in UEFI mode (I still can't find anywhere to control if it does or not).

Still boots right into Windows.

> **darkod said:**
> The cd you can boot in both modes, about usb I'm not sure if it depends how it was created. I don't use uefi and don't have many details except few things mentioned here on the forum.

Windows should have installed in uefi automatically if uefi is enabled on the board. You can test also if you boot the ubuntu usb in live mode (doesn't matter uefi or not), and in terminal execute:
[code]sudo parted -l[/code+

If it says the partition table on the hdd is GPT, then windows is in UEFI because it can only work with gpt on uefi. Otherwise, it works with msdos table in the standard bios boot mode.

Here's the output:

[B]ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: _msdos_

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   74.1GB  74.0GB  primary   ntfs
 3      74.1GB  500GB   426GB   extended
 5      74.1GB  492GB   418GB   logical   ext4
 6      492GB   500GB   8478MB  logical   linux-swap(v1)


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  8005MB  8005MB  primary  fat32        boot, lba[/B]

So partition table is MSDOS, what now?

---

### Post by ambient007 on 2012-08-28
By the way, the windows installation was done from a startup USB created by 'Universal USB Installer' using a Windows 7 Ultimate ISO.

> **drmrgd said:**
> You actually might be OK with the way you've set up.  In my ASUS UEFI BIOS, there is an option to boot the USB device either in BIOS mode or UEFI mode.  Perhaps you don't get that option in your BIOS and boot into UEFI by default?

The best thing to do would be to run the "Create Bootinfo Summary" portion of the Boot Repair package:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

With that we can have a look to see how Windows is setup and what the boot partition looks like.  It might be a simple matter of configuring Grub to pick up the slack.  Please post the results of the Bootinfo Summary here with code tags and we'll see if you need to reinstall or if you're already OK.

Thanks for your reply, I'll look into this now.

---

### Post by darkod on 2012-08-28
In that case you are not using uefi, since windows needs gpt for uefi.

If possible, try to disable uefi in your BIOS.

Try running the boot-repair suggested, it should understand the setup and do everything for you.

---

### Post by ambient007 on 2012-08-28
> **darkod said:**
> In that case you are not using uefi, since windows needs gpt for uefi.

If possible, try to disable uefi in your BIOS.

Try running the boot-repair suggested, it should understand the setup and do everything for you.


Will do.

Like I said before, I don't have any data on this computer yet (I just built it yesterday).
If there's some way to reinstall windows using UEFI, I can do that if it's easier...

---

### Post by ambient007 on 2012-08-28
Here's the Bootinfo summary: [http://paste.ubuntu.com/1172001/](http://paste.ubuntu.com/1172001/)

I guess I'll try running a repair.

---

### Post by ambient007 on 2012-08-28
Here's the new bootinfo summary following the repair: [http://paste.ubuntu.com/1172020/](http://paste.ubuntu.com/1172020/)

Gonna reboot now, wish me luck!

---

### Post by ambient007 on 2012-08-28
It works!!

darkod & drmrgd, thanks so much for your help!

---

### Post by drmrgd on 2012-08-28
Great!  Glad that worked for you.  By the looks of things, it looks like both systems were installed in BIOS mode, just for future reference.  So, if you ever want to add any other OSes to the chain, definitely stick with BIOS mode for those installs as you can't mix and match UEFI and BIOS unfortunately.

Good luck with the new build!

---

### Post by ambient007 on 2012-08-28
> **drmrgd said:**
> Great!  Glad that worked for you.  By the looks of things, it looks like both systems were installed in BIOS mode, just for future reference.  So, if you ever want to add any other OSes to the chain, definitely stick with BIOS mode for those installs as you can't mix and match UEFI and BIOS unfortunately.

Good luck with the new build!

Thanks man!

---

