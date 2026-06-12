---
title: "cannot boot from usb while downgrading"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by itiel on 2016-11-23
hi, i get ubuntu 16 on my computer (Asus) , but it's too heavy for it so i've been trying to downgrade to 14.4 32-bit. 
the problem is that for some reason i can't boot from my usb. i've tried in many different ways (downloading iso from different sources, booting my usb with rufus, usb universal, unetbootin etc.) but it won't work. i've go to BIOS and changed it so that it will boot from the USB but it's still wont work. when i let the USB boot be the only option, it's coming back to the BIOS. anyone have any clue?? thanks.

---

### Post by C.S.Cameron on 2016-11-23
Does the USB work on other computers?
If it is an older computer? then there should not be a problem with UEFI or Secure Boot?
Perhaps try installing with mkusb, it boots with grub2, not syslinux.

---

### Post by Bucky Ball on 2016-11-23
As above. Also, I've had this problem when the USB won't boot when set in the BIOS but will boot when chosen from the device boot menu.

So, on many machines, if you hit F12 when you would normally hit the BIOS key at boot you will get to a device boot menu. If the USB is there, hit it and see what that gives.

---

### Post by Bucky Ball on 2016-11-23
As above. Also, I've had this problem when the USB won't boot when set in the BIOS but will boot when chosen from the device boot menu.

So, on many machines, if you hit F12 when you would normally hit the BIOS key at boot you will get to a device boot menu. If the USB is there, hit it and see what that gives.

---

### Post by sudodus on 2016-11-24
If Ubuntu is too heavy, it is a good idea to get a community flavour of Ubuntu ***16.04.1 LTS*** with a lighter desktop environment, ***Lubuntu*** with the ultra light LXDE or ***Ubuntu MATE*** and ***Xubuntu*** with the medium light MATE and XFCE desktop environments. See the following links and links from them to get tips how to make the computer boot from USB.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

