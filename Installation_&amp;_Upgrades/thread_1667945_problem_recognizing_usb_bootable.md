---
title: "problem recognizing usb bootable"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by poleapple on 2011-01-15
I currently am dual booting linux mint and windows 7. My only hard drive is partitioned in two, one for linux mint and one for windows 7. I installed linux mint with a usb bootable.

I want to replace my linux mint with ubuntu, however, my the usb bootable ubuntu isn't being recognized. I restart the laptop with the usb inside, but it just goes to the grub screen that lets me choose between linux mint or windows 7. The boot order has USB in first position as well. I used the usb creator as suggested on the ubuntu downloads page to create a usb bootable too.  I've done this installation before with both ubuntu and mint... but now it's not working.

Anyone know why?

Thanks for the help.

---

### Post by C.S.Cameron on 2011-01-15
If all else fails you should be able to boot linux mint plug in the usb and do an update-grub.

The usb drive should then be listed in your grub menu.

---

### Post by poleapple on 2011-01-15
What do you mean update-grub? I wish to replace mint with ubuntu though...? Are there any other solutions? 
Yah, I can go into linux mint.

---

### Post by poleapple on 2011-01-15
Oh I see... how do I perform update-grub on linux mint? Is it the same as ubuntu?

---

### Post by C.S.Cameron on 2011-01-16
Boot linux mint plug in the usb and open terminal and type "update-grub".
The next time you  boot grub should have an option for the flash drive, choose that and install Ubuntu over Mint.

---

### Post by poleapple on 2011-01-16
I ran sudo update-grub...

Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

then I rebooted and the screen where I can select between mint and windows 7, I couldn't see usb option...

---

### Post by poleapple on 2011-01-16
I ran sudo update-grub...

Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

then I rebooted and the screen where I can select between mint and windows 7, I couldn't see usb option...

---

### Post by poleapple on 2011-01-16
I ran sudo update-grub...

Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

then I rebooted and the screen where I can select between mint and windows 7, I couldn't see usb option...

---

### Post by poleapple on 2011-01-16
I ran sudo update-grub...

Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

then I rebooted and the screen where I can select between mint and windows 7, I couldn't see usb option...

---

