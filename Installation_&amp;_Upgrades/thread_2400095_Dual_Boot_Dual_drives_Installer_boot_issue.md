---
title: "Dual Boot Dual drives Installer boot issue"
date: 2018-09-02
forum: Installation &amp; Upgrades
---

### Post by DebilMudak on 2018-09-02
I'm trying to install Ubuntu 16.04 and I'm experiencing difficulties.

I have multiple SSD's and I have Windows 10 installed on one. I would like to install Ubuntuon another SSD. I have created a bootable USB-stick using Ubuntu installation ISO. When I start the computer and enter UEFI BIOS, the usb-stick is seen there but when I try to BOOT it, the screen simply flashes and returns to UEFI settings screen. I'm pretty sure I've installed Windows in UEFI mode and I tried disable quick boot. I have not tried to disable secure boot, as it seems a bit more complicated matter. What could be wrong?

Windows 10, Ubuntu, CPU and everything else are 64-bit.

---

### Post by oldfred on 2018-09-02
Moved to your own thread. Please do not high jack another users thread as issues are different.

What brand/model System?
What video card/chip?

How did you create USB bootable installer? What install tool/instructions did you use.
Issue could be bad download, did you check ISO with md5sum?
Or could be incorrectly installed to flash drive.
Or needs boot parameters.

       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
      [/URL]
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]        
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by DebilMudak on 2018-09-02
I didn't want to create a new thread as I thought my problem was similar so I thought I'd try conserve bit-space. So much for trying to be thoughtful.

I created the bootable thumb drive using RUFUS and the installation iso-image downloaded from Ubuntu's website. I haven't checked the md5sum of it though.
The file system of the thumb drive is NTFS actually if there's an issue but I'll create a new bootable drive and see if that'll help.

---

### Post by oldfred on 2018-09-02
I did not think Rufus created NTFS. I have never used it.

To boot with UEFI, you have to have FAT32 with boot flag and /EFI/Boot/bootx64.efi. Both Windows & Ubuntu or any UEFI bootable system from an external drive use that path & filename as that is UEFI standard.

---

### Post by DebilMudak on 2018-09-03
Rufus can format to NTFS, I remember selecting that option. Anyway I recreated the thumb drive using FAT32 and it works now, I am able to install Ubuntu.

---

### Post by oldfred on 2018-09-03
With multiple drives only use Something Else or disconnect all but the drive you are installing Ubuntu into.

See link below in my signature for more UEFI install info.

---

