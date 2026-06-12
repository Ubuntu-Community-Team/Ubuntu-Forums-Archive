---
title: "Ubuntu 12.04 64 bit usb install does not boot"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by L3TH4LBR on 2013-05-06
Hello,

I am trying to create a Live USB drive with Lubuntu 13.04 on it (with persistence) using Lili (Windows). It's a Sandisk 32GB USB3 flashdrive, and I used Lili on a Windows 7 Laptop (USB2) to install it with 640MB persistence (for now). However, when I try to boot, all it does is giving a black screen with a blinking cursor, even when I use my other computer on the USB 3 port.

The flashdrive is fully partitioned as FAT32 using EaseUS Partition Manager (Windows 8).

Did I do something wrong? Or is this a known issue and should I use another version of Lubuntu instead?

Thank you in advance.

Edit: Sorry for such a specific question, but I really need a live set-up like this because I don't want a dual boot.

---

### Post by kero4 on 2013-05-07
I was having an issue as well installing lubuntu 13.04 from usb so I resorted to CD install and it worked. It was quite odd as I never had that issue on any lubuntu version before this installing via USB.

---

### Post by Lightning Dragon on 2013-05-07
Hi,

Last night I was also trying to install Lubuntu via Sandisk...and found out the USB brand is mostly unsupported (tested three of them!). I switched to a Toshiba USB and redid the install and it worked flawlessly. So it is your Sandisk USB. Do you have any other USB sticks lying around that you could use?

---

### Post by mörgæs on 2013-05-08
There's some advice on Sandisk in the link in my signature.

---

### Post by L3TH4LBR on 2013-05-21
I don't have any other flashdrives, so I'll try to fix my external Harddisk. If that doesn't work out either, I'll just have to see. Thanks a lot for your help!

Edit: Are flashdrives from corsair (USB 3.0 32GB) any good?

---

### Post by L3TH4LBR on 2013-06-11
*bump*

I discovered what the problem is, it´s NOT my flashdrive, since an external HDD has the same issues.

It seems that my setup doesn´t support UEFI boot.

I installed Ubuntu on my flashdrive normally, including the bootloader. However I read that UEFI only supports booting from FAT32.

Could anyone tell me how I can repartition my flashdrive or harddrive so that is DOES support booting from UEFI?

P.S. I am working with Ubuntu 12.04.2 LTS 64bits instead of Lubuntu.

---

