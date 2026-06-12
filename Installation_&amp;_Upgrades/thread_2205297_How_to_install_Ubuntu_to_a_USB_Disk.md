---
title: "How to install Ubuntu to a USB Disk?"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by hhtmp88 on 2014-02-13
Dear all,

as titled.

Thanks for any kind of help!

---

### Post by claracc on 2014-02-13
Please, see: [https://help.ubuntu.com/community/Installation#Installing_on_external_or_RAID_hard_disks](https://help.ubuntu.com/community/Installation#Installing_on_external_or_RAID_hard_disks)

---

### Post by sudodus on 2014-02-13
*Edit*: Do you mean to make a live or persistent live USB drive, or do you mean to make an 'installed system' booting with grub on a USB drive?

-o-

I find it easy to use ***mkusb*** according to this

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

You get general instructions and a lot of links at this Ubuntu wiki page

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and there is a detailed help page for ***Unetbootin*** at this link

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/") 

See also this thread, [what is the simplest way to burn an iso to a usb]("http://ubuntuforums.org/showthread.php?t=2205097")

---

### Post by C.S.Cameron on 2014-02-13
If you want to do a Full install to USB,
Disable your internal HDD,
Plug in your USB device,
Install using Live CD or Live USB.

If you also want to use the device for file storage or transfer on a Windows machine:
Make the first partition NTFS or FAT32 using the "Something else" option while installing.

You might also want to check out Sudodus' OBI, it uses an image file to install and is fast.

---

