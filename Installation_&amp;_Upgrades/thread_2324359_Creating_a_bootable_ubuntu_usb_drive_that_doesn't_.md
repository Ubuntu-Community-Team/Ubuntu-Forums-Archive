---
title: "Creating a bootable ubuntu usb drive that doesn't boot into a blank screen"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by malte2 on 2016-05-13
Hi!

I am working on a Macbook Pro but use Ubuntu for hosting my web applications. So the IT department dropped an old Core 2 Due Intel Dell box. So I downloaded the newly released Ubuntu 16.04 LTS server ISO and used unetbootin to create a bootable usb drive. I am able to see the BIOS, then the loading ubnkern/ubninit.... and then just a blank screen, screen is on but get completely blank black screen. So I check the md5 sum of the image (is correct) and then use dd to create the ubuntu 16.04 bootable usb drive thinking it is unetbootin that is causing the black screen. Same result. Black screen.

So I ran into this page: [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

These workaround are not really actionable for me, e.g. set gfxpayload=text, without any reference where to set that. I suspect I would have to make those changes within the ISO image before turning forging a bootable ubuntu usb drive from it? Could someone give me an idea of how I would implement those workarounds and create a bootable ubuntu usb drive that doesn't boot into a completely blank screen?

---

### Post by sudodus on 2016-05-13
Welcome to the Ubuntu Forums :-)

It seems you have problems with the graphics, but it could also be the wifi. Please specify the

- graphics chip/card
- wifi chip/card

-o-

If there is nvidia graphics, it may help with the boot option nomodeset, and then you can install a proprietary driver.

If there is intel graphics, you can try with 'xserver-xorg-video-intel' installed, so you can try according to the following link,

[New Lubuntu tarball with 'xserver-xorg-video-intel' for Intel graphics](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13487384#post13487384)

That link describes the method with a tarball, but also another method that is easier, but can only install to the whole drive (no dual boot), to clone from the corresponidng compressed image file. It is straightforward with [mkusb](https://help.ubuntu.com/community/mkusb), but also posssible by extraction with a decompression tool and cloning with any tool, for example dd. So this method suits very well to create a USB boot drive with an installed system.

If you want a system, that boots in UEFI as well as in BIOS mode, you can use the method described in the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by echotech2 on 2016-05-14
How old is "old Core 2 Due Intel Dell"?  My computer with a BIOS dated 2006 Has AHCI options "Enabled" and "Disabled".  At boot time I get a message "This AHCI version supports Hard Drive and CD-Rom Only" (but it will boot a DVD).  With AHCI enabled it won't boot a USB stick but it will boot the stick if AHCI is disabled.

---

