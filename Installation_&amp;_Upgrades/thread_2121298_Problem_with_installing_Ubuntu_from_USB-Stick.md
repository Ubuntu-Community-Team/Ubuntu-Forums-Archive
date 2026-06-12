---
title: "Problem with installing Ubuntu from USB-Stick"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by ungeruehrt on 2013-03-01
Hi there,
some months ago I installed parallel to windows 7 (on a different partition of cause) ubuntu. There were no problems with ubuntu at this time but with windows 7 so that I had to reinstall Windows some weeks ago (which caused that just Windows started because Grub hasn't been installed afterwards). Today I wanted to install/repair ubuntu from my usb-stick so I used unetbootin and the .iso for ubuntu 12.04 64bit from ubuntu.com, but when I tried to boot from usb stick, there was immediately some error message:
> 
Try (hd0,0): NTFS5: No grdlr
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd1,0): NTFS5: No grdlr
Try (hd1,1): NTFS5: No grdlr
Try (hd1,2): Extended;
Try (hd1,3): EXT2:
I'd be happy if you could help me fixing this error so that I'm able to install ubuntu as a second os on my laptop! Thanks for your efforts :)

---

### Post by oldfred on 2013-03-02
The no grdlr is grub4dos which is usually from EasyBCD or wubi, so did you have EasyBCD. And then it is booting from Hard drive not from USB. So confirm that you downloaded ISO correctly and extracted it not copied it to flash drive correctly.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

