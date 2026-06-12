---
title: "Installing Ubuntu on an USB-drive as a live OS (for bitcoin storage etc)"
date: 2021-05-04
forum: Installation &amp; Upgrades
---

### Post by smith73 on 2021-05-04
I was searching a bit on how to use regular 32/64 GB USB-drives (with no hardware-based encryption) for bitcoin storage, 
and several tutorials mentioned the necessity to install a bitcoin wallet such as Electrum on a live OS like Ubuntu installed 
on a USB-stick. And there was a link to an oficial Ubuntu dowlnload page with Desktop, Server and Raspberry Pi Ubuntu versions.
Maybe an option of "Try Ubuntu" was implied in which a user can install programs on a hard drive in some demo mode,
though for bitcoin storage it seems unlikely.

I can't figure out how you can install an Ubuntu Desktop for example as a bootable live OS on an USB-drive from another
USB-drive wherein I've already installed a bootable Ubuntu .iso for Ubuntu installation. I suppose there will not be such
an option in BIOS to choose to install Ubuntu not on a computer's hard drive, but on another connected USB-drive.

Or are there some tutorials on how to install an Ubuntu distro as a live OS on a bootable USB-drive connected to a PC?

---

### Post by tea for one on 2021-05-04
Your post was a little bit confusing - probably due to terminology but let's proceed.

Do you mean:-

A portable USB device using Ubuntu in a live session with persistent storage but [COLOR="#0000FF"]without[/COLOR] a user?
A portable USB device using Ubuntu in a live session with persistent storage but [COLOR="#0000FF"]with[/COLOR] a user?
A permanent Ubuntu installation on a hard drive?

All are possible.

Whether they will satisfy your requirement for bitcoin storage - I have no idea.

Here are some websites for further info:-

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

---

### Post by C.S.Cameron on 2021-05-04
Not sure from your description but it sounds like you need a Persistent Live USB. (A Live USB that saves changes boot to boot).

Windows tools that can be used to make a Persistent Live USB include Rufus, ([https://rufus.ie/en_US/](https://rufus.ie/en_US/)), UNetbootin, ([https://unetbootin.github.io/](https://unetbootin.github.io/)), Universal USB Installer, ([https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)), YUMI, ([https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)) or Ventoy, ([https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html)).

I would try Rufus first.

Linux tools that can be used to make a Persistent Live USB include: mkusb, ([https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)), UNetbootin and Ventoy.

I would try mkusb first.

---

