---
title: "Problems while installing Ubuntu 13.10 x64 from USB"
date: 2014-03-14
forum: Installation &amp; Upgrades
---

### Post by gagoalaverdyan on 2014-03-14
[COLOR=#333333][FONT=UbuntuRegular]I am trying to install Ubuntu 13.10 64bit from a USB stick (I created the LiveUSB as in the official documentation on Ubuntu site and it gave me no errors) on my PC. Everything goes well before the Ubuntu splash screen, but the splash screen stays forever. Then I tried booting with parameters like nomodeset noacpi etc. but that didn't work too. I tried making different flash drives and checked MD5 file of the iso image with the one on Ubuntu official site everything is OK. Then i tried booting with noquiet and nosplash options and saw this in terminal:[/FONT][/COLOR]
Begin: Mounting root file system ... Begin: Running /casper-premount ...
 done
 calling: test-builtin
 Error reading /lib/udev/hwdb.bin: No such file or directory
 load module index
 unload module index

usb 1-5: reset high speed USB device using ehci_hcd and address 3
usb 1-5: reset high speed USB device using ehci_hcd and address 3
usb 1-5: reset high speed USB device using ehci_hcd and address 3
usb 1-5: reset high speed USB device using ehci_hcd and address 3
[COLOR=#333333][FONT=UbuntuRegular]The last line endlessly repeats in 4-5 seconds. I used to install Ubuntu 9.04-11.10 before and everything was ok then.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What could be the problem?[/FONT][/COLOR]

---

