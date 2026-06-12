---
title: "Live USB only works with BIOS set to EUFI but Win10 is installed as Legacy -"
date: 2021-06-03
forum: Installation &amp; Upgrades
---

### Post by teaguepatrick on 2021-06-03
I'm trying to set up a dual boot on my Lenovo Yoga 710-11IKB. It currently has Windows 10 installed with Legacy BIOS and I'd like to keep it. 

My boot order has my USB as #1 and the Live USB is confirmed to work on other PCs but it won't boot whatsoever unless I switch my BIOS to EUFI. Then it works! 

But I don't want to install Ubuntu with EUFI because I have Windows 10 in Legacy!

Why won't it boot Live USBs when the BIOS is set to boot from Legacy? At this point I think I've tried every option possible in the BIOS and the only way I can get the LIve USB to boot is if I set my BIOS to EUFI, yet I want Ubuntu alongside a Win10 Legacy install. 

Help?

---

### Post by Impavidus on 2021-06-03
How was the live usb created? Some tools (notably rufus) create a live usb that boots in either uefi or legacy mode, but not both.

Dual booting Windows 10 and Ubuntu in legacy mode is a bit fragile, in particular on a single harddrive. Make sure you've got a repair drive for Windows and keep your Ubuntu live disk for repairs. Best to have those anyway. Unless you can change your Windows 10 to uefi.

---

### Post by teaguepatrick on 2021-06-03
I've made the Live USB in RUFUS, UNetbootin, and Startup Disc Creator and the result is the same among the three - boots in EUFI and get stuck in an endless loop in Legacy. 

I don't care if windows is in Legacy or EUFI. I rarely use windows anyways. I just need a dual boot and I don't care how I get there so if EUFI is more stable anyways, and it's possible to switch my Windows install from Legacy to EUFI, then I'm all game. Is it hard? Is there a good guide to walk me through it? 

THANK YOU for trying to help me out because I don't know what to do at this point.

---

### Post by teaguepatrick on 2021-06-03
I changed WIN10 to EUFI and I'm Live booting USBs like it's going out of style. Thank you for your help! How do I mark this as solved! THANKS.

---

### Post by sudodus on 2021-06-03
Try to make the USB pendrive bootable both in BIOS mode and UEFI mode with the tool **[mkusb](https://help.ubuntu.com/community/mkusb). Use mkusb version 12 alias mkusb-dus** and create a 'persistent live' system in the USB pendrive.

I know that you don't need it to be persistent, but the boot structure is different from what you get when cloning (for example with the Startup Disk Creator), and it might boot successfully in BIOS mode.

In this case, **select 'live' in the grub menu** boot [again?] and go ahead to install Ubuntu.

[hr][/hr]
Please tell us also which version of Ubuntu that you are trying to install.

---

### Post by sudodus on 2021-06-03
> **teaguepatrick said:**
> I changed WIN10 to EUFI and I'm Live booting USBs like it's going out of style. Thank you for your help! How do I mark this as solved! THANKS.

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

(It will still be possible to add new posts and/or edit old posts.)

---

### Post by tea for one on 2021-06-03
> **teaguepatrick said:**
> I changed WIN10 to EUFI and I'm Live booting USBs like it's going out of style. 

UEFI 1 - Legacy 0

Surely, that can't be right?
Where's VAR?

I mean [COLOR="#0000FF"]Video Assistant Referee[/COLOR] rather than [COLOR="#FF0000"]/var[/COLOR]

---

