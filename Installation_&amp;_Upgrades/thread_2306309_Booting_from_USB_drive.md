---
title: "Booting from USB drive"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by dogdeblack on 2015-12-14
Hello fellow users that probably are way more experienced than I am.I´d like to know how I´d be able (if I´m able at all) to change grub´s configuration while inside of lubuntu to make it so next time it boots up it ends up booting my USB drive.I´m using lubuntu 14.10

---

### Post by sudodus on 2015-12-14
0. The version 14.10 has passed end of life. Do not use it!

[hr][/hr]
1. Do you want to boot your USB drive? You can do that by chainloading with the 40_custom method. See this link

[Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

Or have I misunderstood what you want?

[hr][/hr]
But often it is possible to press a hotkey, (different for different computers), and boot directly to USB.

From [Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB):

Remove all unneeded USB items, but keep the network cable attached.

Insert the bootable USB flash drive that you just created in your target computer and restart it. Most newer computers can boot from a USB flash drive. If your computer does not automatically do so, you might need to edit the BIOS settings.

Restart your computer, and watch for a message telling you which key to press to enter the BIOS setup. It will usually be one of F1, F2, DEL, ESC or F10, you can search yours hardware on [boot-keys.org](boot-keys.org). Press this key while your computer is booting to edit your BIOS settings. (On HP Mini Netbooks, they correct key is usually F9.)

Instead of editing BIOS settings, you can chose a boot device from the boot menu. Press the function key to enter the boot menu when your computer is booting. Typically, the boot screen displays which key you need to press. It maybe one of F12, F10. Note: with soFromUSBStick#UEFI]me motherboards you have to select 'hard disk/USB-HDD0' to choose the USB flash disk. It may work like this because the system sees the USB drive 'a mass storage device' as a hard disk drive, and it should be at the top of the boot order list.

So you need to edit the Boot Order. Depending on your computer, and how your USB key was formatted, you should see an entry for "removable drive" or "USB media". Move this to the top of the list to make the computer attempt to boot from the USB device before booting from the hard disk.

[hr][/hr]
If you run the computer in UEFI mode, things can be more complicated. See this link and links from it:

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by C.S.Cameron on 2015-12-14
I recall doing an update-grub while running Ubuntu with a USB plugged in, it added the USB stick to my grub menu.
Not sure if this only works for grub boot USB sticks or for syslinux boot sticks also.

---

### Post by dogdeblack on 2015-12-15
Yeah I´ll try what you first said.I know you can change it in the Bios but the reason I want to change the boot in grub is exactly because I dont have the Bios password as I changed it years ago :/

---

### Post by dogdeblack on 2015-12-15
I dont get the grub menu when I boot it just directly boots up lubuntu

---

### Post by sudodus on 2015-12-15
Good luck with chainloading :-)

---

### Post by C.S.Cameron on 2015-12-15
It is easy to clear a BIOS password, see example:

[http://www.computerhope.com/issues/ch000235.htm](http://www.computerhope.com/issues/ch000235.htm)

---

### Post by C.S.Cameron on 2015-12-15
From Google:

On a new installation of Ubuntu 9.10 or later with no other installed operating systems, GRUB 2 will boot directly to the login prompt or Desktop. No menu will be displayed. Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.

---

### Post by sammiev on 2015-12-15
> **C.S.Cameron said:**
> It is easy to clear a BIOS password, see example:

[http://www.computerhope.com/issues/ch000235.htm](http://www.computerhope.com/issues/ch000235.htm)

Been there on a few computers drop off at the door.

It works great.

---

