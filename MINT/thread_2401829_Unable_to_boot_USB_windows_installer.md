---
title: "Unable to boot USB windows installer"
date: 2018-09-23
forum: MINT
---

### Post by turtlefriend on 2018-09-23
I'll preface this by mentioning I'm quite the rookie when it comes to Linux.
Using Linux Mint Serena. 
Even though I set the USB for boot priority in the bios, it ignores this and starts like usual. I've tinkered a bit with what I thought might be the issue, primarily by deactivating secure boot, but to no avail. I've tried the USB on another computer and it worked fine. 
Appreciate any help.

---

### Post by Quarkrad on 2018-09-23
Have you tried hitting F12 during the bios/boot process?  On some machines this comes up with a list of devices to boot to - you can select the USB.

---

### Post by turtlefriend on 2018-09-23
Yes, the screen goes black for a few seconds and then it starts like normal. I don't get the option to choose which device to boot, as I do in my other computer.

---

### Post by jeremy31 on 2018-09-23
Moved to MINT

---

### Post by westie457 on 2018-09-23
Give this a try. [https://ubuntuforums.org/showthread.php?t=2401741&p=13802767#post13802767](https://ubuntuforums.org/showthread.php?t=2401741&p=13802767#post13802767)

---

### Post by turtlefriend on 2018-09-23
> **westie457 said:**
> Give this a try. [https://ubuntuforums.org/showthread.php?t=2401741&p=13802767#post13802767](https://ubuntuforums.org/showthread.php?t=2401741&p=13802767#post13802767)

I don't really see how this has anything to do with my issue. I don't have windows installed or anything like that. 

Some more information:
Mint boots although I get some errors and I previously didn't have sound, although through trial and error I managed to fix that. 
I am trying to install Windows 7. 
 The USB is recognized in the BIOS. It appears both under USB port and boot priority.

I was able to install the current software I'm using, that is, Mint, through the same method before. The installation worked fine then and I don't know why it wouldn't work now, the only difference is that I have Mint now. The USB also boots fine on other computers.

---

### Post by ajgreeny on 2018-09-23
Is your hardware using UEFI or legacy BIOS?

Pre-installed Windows 7 was usually installed using BIOS, not UEFI and it is possible that your USB is for BIOS only, not bootable on UEFI.
Did you create the USB yourself or did you get it from somewhere else, pre-made?
The requirements for a bootable Windows USB are a bit different from those for Ubuntu/mint and you could be tripping up on that if your machine uses UEFI.
See [https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/Windows-7-UEFI-Installation.pdf](https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/Windows-7-UEFI-Installation.pdf)

---

### Post by turtlefriend on 2018-09-23
I believe my system uses UEFI
> ls /sys/firmware/efi/
config_table  esrt              fw_vendor  runtime-map  vars
efivars       fw_platform_size  runtime    systab

Also, the USB under boot priority (in the BIOS) mentions being UEFI as well. 

I made the USB myself and I tested it on a different computer and it worked (this other computer was running Windows, not Linux) so I don't think the problem is with the USB, but I don't really know.

---

### Post by westie457 on 2018-09-23
This guide for customizing the ISO could be adapted to be used within Linux Mint. [https://www.sevenforums.com/installation-setup/321097-how-install-windows-7-uefi-mode-usb.html](https://www.sevenforums.com/installation-setup/321097-how-install-windows-7-uefi-mode-usb.html)

---

### Post by turtlefriend on 2018-09-23
Well, scrap windows 7, figured I'd just go back to windows 10, since that should work. Problem is, now the USB doesn't even appear in the BIOS. I'm stumped.

---

