---
title: "Problems booting from USB"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by mitchnufc on 2012-10-04
Hi,

I am trying to install Ubuntu from a USB device, I access my laptops setup via F2 and select boot and it has three options Hard drive,  USB Flash device and Network, however when I select USB nothing happens does anyone have any ideas and it never boots from USB if its connected.

---

### Post by doktorOblivion on 2012-10-04
Two things to check, make sure you have a bootable usb image using tools you can find in these forums, second make sure the usb mem device is plugged while you are making your boot device selection in your BIOS.

---

### Post by oldfred on 2012-10-04
My BIOS has many options to boot USB devices, but my USB flash drive boots from the hard drive menu, not USB menu.

Flash has to be correctly configured as bootable for BIOS to see it.

---

### Post by mitchnufc on 2012-10-04
I've tried all of these options and not having any luck

---

### Post by doktorOblivion on 2012-10-04
How was the bootable image on your USB built?  How did you create your bootable image, using a known tool, if so, which one?  Provide more info...its hard to answer in a vacuum.

---

### Post by mitchnufc on 2012-10-04
> **doktorOblivion said:**
> How was the bootable image on your USB built?  How did you create your bootable image, using a known tool, if so, which one?  Provide more info...its hard to answer in a vacuum.

I downloaded the 12.04 ISO file and used Universal USB Installer

---

### Post by oldfred on 2012-10-05
That should work. But some for whatever reason have issues with one or the other ways of writing USB flash drives.

Verify that ISO is good with md5sum.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by mitchnufc on 2012-10-05
> **oldfred said:**
> That should work. But some for whatever reason have issues with one or the other ways of writing USB flash drives.

Verify that ISO is good with md5sum.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Thanks for the help, everything is working now it was a problem with my Scan disk USB stick I believe.

---

