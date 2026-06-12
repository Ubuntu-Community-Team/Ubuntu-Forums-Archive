---
title: "USB operating system"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by Crowley666 on 2013-09-29
Has anyone installed ubuntu on to a usb successfully??? any tip for me??

---

### Post by Crowley666 on 2013-09-29
Just as it says, best  version of ubuntu for usb drive???? If anyone has some experience of this?????

---

### Post by heir4c on 2013-09-29
(Sorry for my bad English)

Yes, I do.
Just install it like you do on a HD. Don't forget to create a swap partition.
If you have usb3 on your motherboard use a usb3 so it will work faster. But if you boot up on a older PC/Laptop there is a change he is not recognised by the bios directly. So I had to wait till de cdrom-drive was recognised by the bios before I plug in the usb3. (You heard the cdrom "clicking")

---

### Post by oldfred on 2013-09-29
USB hard drive or USB flash drive? USB2 or USB3 port? USB port is a bit of a bottleneck. 

Still comes down to what hardware, cpu, RAM and video card you have. If hardware is limited Lubuntu or Xubuntu may be a bit better.

I have full install in a 32GB flash drive and it works. Bit slow loading, but once loaded runs fine. Writing is very slow. I have found even with my USB2 ports a USB3 flash is about 10% faster.
But I also do not use Unity but install gnome fallback as my systems are 6 years old and while both run Unity it requires more Video and RAM to run well.

---

### Post by Crowley666 on 2013-09-29
Usb flash drive, the laptop is not that powerful, just a basic compaq, think the flash is 8 or 16, think more than 4 is enough, which linuxlive usb creator do I use, is it, portable, persistence, or 2.8.19, ???????? thanks for the pointers I'm a bit worried about getting this wrong and wiping my system.

---

### Post by oldfred on 2013-09-29
Full install needs a 8GB minimum, but if just installing the live version 2 or 4GB will work.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2128205](http://ubuntuforums.org/showthread.php?t=2128205)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

 Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

### Post by QIII on 2013-09-29
Threads merged.  Please do not post duplicate threads in different parts of the forum.  It dilutes the community's efforts to help by spreading out the answers -- as happened here.

---

### Post by sudodus on 2013-09-30
> **Crowley666 said:**
> Usb flash drive, the laptop is not that powerful, just a basic compaq, think the flash is 8 or 16, think more than 4 is enough, which linuxlive usb creator do I use, is it, portable, persistence, or 2.8.19, ???????? thanks for the pointers I'm a bit worried about getting this wrong and wiping my system.

*Oldfred* already gave you a lot of valuable links. I can add a few more, that show alternatives.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")
[One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

---

### Post by ubfan1 on 2013-09-30
Extra care is needed if you have a UEFI machine, particularly one with Ubuntu already installed on the hard disk.  Installing to USB definitely has problems with selecting the bootloader location -- used to be sufficient to just select the device as the location, then I thought the target EFI partition was working in 13.04, but in 13.10 (Sept 20), the partition selection did not work, the files were written to the hard disk, and with grub.cfg now pointing to the USB, the hard disk ubuntu no longer worked.  Easy enough to fix, since I had a backup grub.cfg sitting there, but had to file a bug # 1229488.  Do back up your files and the EFI files before installing.  Do check the size of the disk you select, it should be the usb size -- the disk numbering/lettering seems not to be as stable as before 12.04.  I find without swap, I can still install to a 4G stick.

---

