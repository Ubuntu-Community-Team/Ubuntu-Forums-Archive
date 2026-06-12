---
title: "write a bootable USB from Jammy Jellfish ISO on Bionic Beaver (with existing tools)."
date: 2022-11-11
forum: Installation &amp; Upgrades
---

### Post by bitrat2 on 2022-11-11
Hi,

I realise this question has been asked before, but there are also equally many different answers..

For example, there is no 'Startup Disk Creator' on my system.  Also, 80% of them demonstrate making a boot disk using various random burner apps, none of which I'm going to use.

My plan so far is to create a bootable FAT partition on a 16G USB and copy the ISO to it with:

```
sudo dd if=ubuntu-22.04.1-live-server-amd64.iso of=/dev/sdc bs=1M status=progress
```

I tried this once, but rather than booting I ended up at a grub prompt.  I tried using grub commands (*root= ..  chainloader ...*)  but couldn't find the efi file on the drive...

Cheers,
bitrat

---

### Post by oldfred on 2022-11-11
The dd command writes a hybrid DVD/flash drive which should work.
If UEFI system, you can create FAT32 partition and just extract ISO to it.

If you used dd, you have to erase partition table area on drive as the hybrid write puts random data into partition table and then partition tools do not correctly see drive.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)
or to clear just partition table area. Where sdX is your drive, sdb, sdc etc.
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1

I used it for this ISO to my SSD.
sudo apt-get install p7zip-full
p7zip Note no space after -o  or gzip?
7z x [ISO_NAME]  -o[DESTINATION_FOLDER]
sudo 7z x ~/ISO/impish-desktop-canary-amd64.iso -o/media/fred/EFI_SSD64

---

### Post by C.S.Cameron on 2022-11-12
If you **extract** the ISO to a FAT32 partition it will boot using UEFI. No other programs required.
I believe that you need to install GRUB to boot an ISO.
Sudodus has produced an image file that makes booting ISO files real easy: [https://askubuntu.com/a/1269476/43926](https://askubuntu.com/a/1269476/43926)

---

### Post by C.S.Cameron on 2022-11-12
_if_ should include the full path to the Ubuntu ISO file: ie _if=/path/to/your/isofile_. I think you may be missing one of those slanty things (/) before the ISO name.

---

### Post by bitrat2 on 2022-11-12
Hi,

thanks for these replies.  Lots of good info there.  I may be overcomplicating things since it looks like UEFI is pretty adaptable.

Anyway, I succeeded with the USB boot and looking forward to more experiments.

One thing I found, which may be of interest to some, is that a _DVD_ doesn't work for live boot on my system.  Apparently a service times out because the read is too slow.  I can dig out the link if anyone's interested..

Cheers,
bitrat

---

