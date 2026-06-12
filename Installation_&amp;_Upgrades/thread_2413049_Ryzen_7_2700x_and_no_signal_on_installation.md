---
title: "Ryzen 7 2700x and no signal on installation"
date: 2019-02-20
forum: Installation &amp; Upgrades
---

### Post by jokerxblack on 2019-02-20
Hi guys,I have this configuration:

[LIST]
[*]CPU: Ryzen 7 2700x 
[*]Mobo: Asus x470 gaming 
[*]RAM: 2x8GB 3000 MHz 
[*]GPU: GeForce GT 1030 
[*]Monitor: 4K LG monitor 
[/LIST]
I downloaded the latest stable version of Ubuntu and I did a bootable USB drive with Rufus.
I restarted the PC (with windows 10) and booted the USB stick.
I selected in the grub Install Ubuntu, then there was a loading violet screen and suddenly:
"No signal"
message from monitor and monitor goes off. PC is still on but I can't use the monitor. So I need to force the restart.
Why does this happen? I tried also to reset BIOS configuration and disabled the "xmp" profile, so RAM runs at 2133MHz... but nothing to do.
I think something related with graphics card because my processor Ryzen 7 2700x doesn't have an integrated graphics card, so maybe it switches to the mobo HDMI port instead of the HDMI port in the dedicated GT 1030.
Do you have any advice?

---

### Post by CatKiller on 2019-02-20
> **jokerxblack said:**
> 
[*]**GPU**: GeForce GT 1030
You're probably going to want to try the nomodeset kernel parameter for the install. When you're running it you can use the proprietary driver. 
> 
then there was a loading violet screen and suddenly
You're going to want to use UEFI rather than Legacy when you boot, since it's new hardware and you're also using Windows 10. I believe that gives you a black background rather than the purple.

---

### Post by jokerxblack on 2019-02-21
I solved with nomodeset:

[LIST]
[*]hold down the Shift key when booting starts. 
[*]You will then get a console mode menu. 
[*]Scroll to Install Ubuntu 
[*]Press e to edit that line. 
[*]Move to the end of the line. Delete the text that says quiet splash and then enter nomodesetinstead, ensuring there is a space between the new option and any other option. 
[*]Press F10 to boot. 
[/LIST]
After the Ubuntu installation, Ubuntu will reboot. Press Esc key to enter command prompt. Choose Ubuntu. Press e to edit commands and once again delete the text that says quiet splash and then enter nomodeset instead and boot by pressing F10. In Ubuntu go to the "Software and Updates" and download nVidia proprietary drivers.

---

