---
title: "Booting Ubuntu from USB, &quot;Digital Signature not found&quot;"
date: 2014-04-10
forum: Installation &amp; Upgrades
---

### Post by maikerukonare on 2014-04-10
Hello, I'm an agitated windows 8 user and I have been trying to install Ubuntu on my toshiba satellite laptop. (I also just want to wipe my drive, and switching OS seems to be a good way to accomplish that.) I downloaded the ISO from the Ubuntu site (I got 12.04.4 and 13.10, both receive the error.) I tried each one by using the "Universal-USB-installer-1.9.5.2" software. I chose the ISO, selected Ubuntu, and had it installed to my 4GB USB. 
After having it installed on the USB, the USB comes up as "Install Ubuntu (E:)" under This PC. I powered off the laptop, and pressed F12 while powering it on. I entered set up and changed the boot options to boot from USB first. Once it began booting I immediately got the message "Boot failure : a proper digital signature was not found. One of the files on the selected boot device was rejected by the Secure Boot feature."
Can anyone help me figure this out?

---

### Post by grahammechanical on 2014-04-10
What version of Ubuntu are you using? 32bit or 64bit? You need 64bit.

Windows 8 machines have secure boot enabled by default. This means that you can only install software that has been signed to comply with the secure boot protocol. Ubuntu 64bit comes with a signed Linux kernel and has done so since Ubuntu 12.10. So, you should not have this problem with 12.04.4 or 13.10 if they are 64bit.

Windows 8 machines also have something called UEFI. It replaces BIOS. Again we need a 64bit version of Ubuntu to deal with UEFI. If Windows 8 is installed in EFI mode then Ubuntu must also be installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by maikerukonare on 2014-04-10
I did download 64bit versions. Could I be missing the signed kernel you mentioned somehow?

---

### Post by sudodus on 2014-04-11
You downloaded these versions: ***Ubuntu 12.04.4 LTS or 13.10 (64bit)***. Then you should have a signed kernel.

It should work anyway, but it might help to switch off secure boot and fast boot in an UEFI/BIOS menu.

You can also try Boot Repair according to these links

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

-o-

But you may have problems because you used a tool, that does not work for UEFI (or not at all). Try ***Unetbootin***

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

or to flash the iso file with 

[http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager)

---

