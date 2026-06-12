---
title: "Does 32-bit EFI limit me to 32-bit install of 12.04?"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by szekowski on 2013-10-26
I have an iMac 5,1 (late 2006) that has a 64-bit core2 duo CPU but EFI is 32 bit. I would like to install 12.04 LTS to dual boot with OSX 10.6.8. I have installed rEFInd.

Does my EFI limit me to 32-bit ubuntu? This will be my first linux experience so I am looking for the simplest solution rather than a more complex work-around.

Thanks.

Steve Z

---

### Post by drmrgd on 2013-10-26
According to the Wikipedia page on UEFI, the architecture of the OS bootloader and EFI must match:

> [COLOR=#000000][FONT=sans-serif]UEFI requires the firmware and operating system loader to be size-matched; i.e. a 64-bit UEFI implementation can only load a 64-bit UEFI OS boot loader. After the system transitions from "Boot Services" to "Runtime Services," the operating system kernel takes over. At this point, the kernel can change processor modes if it desires, but this bars usage of runtime services[/FONT][/COLOR][SUP][[18]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-18")[/SUP][COLOR=#000000][FONT=sans-serif] (unless the kernel switches back again). Presently, the only operating system that supports running a kernel that is not size-matched to the firmware is Mac OS X.
[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by oldfred on 2013-10-26
Bit more info on 32bit and the hack Macs use.

[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

---

