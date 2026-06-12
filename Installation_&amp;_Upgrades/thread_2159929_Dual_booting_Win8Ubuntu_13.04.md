---
title: "Dual booting Win8/Ubuntu 13.04"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by sinnet3000 on 2013-07-05
Hello. I have Win8 set with UEFI in a Dell L502X, but Grub-efi didn't get installed. But I can sometimes manage to boot Ubuntu pressing F12 and selecting ubuntu as boot device. I even have problems starting the live usb. It stays in black screen, till one of the times it works. (Seems to have better success rate if I completely shut it down)

Here is my pastebin from Boot-Repair: [http://paste.ubuntu.com/5845894/](http://paste.ubuntu.com/5845894/)

SDA3 appears as Unknown Partition in Gparted but in Gdisk I can see its Microsoft reserved part. I hope this is enough information to help me with the problem.

Thanks a lot

---

### Post by fantab on 2013-07-05
No, the Grub-Efi did not install or perhaps you have installed Ubuntu in 'Legacy mode' and not 'EFI mode'. Boot-Repair should fix this for you. If not condsider reinstalling Ubuntu, only this time you will make sure that you boot Ubuntu DVD/USB in efi mode.  When Ubuntu Installer boots in EFI mode you will see a black screen with options, otherwise it shows the traditional Ubuntu colors.

Have you turned off '[Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")'?

Also it would better for Ubuntu's performance if you have a SWAP partition, if you can spare then 2-4GB should be good.

Good Luck...

---

### Post by sinnet3000 on 2013-07-05
> **fantab said:**
> No, the Grub-Efi did not install or perhaps you have installed Ubuntu in 'Legacy mode' and not 'EFI mode'. Boot-Repair should fix this for you. If not condsider reinstalling Ubuntu, only this time you will make sure that you boot Ubuntu DVD/USB in efi mode.  When Ubuntu Installer boots in EFI mode you will see a black screen with options, otherwise it shows the traditional Ubuntu colors.

Have you turned off '[Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")'?

Also it would better for Ubuntu's performance if you have a SWAP partition, if you can spare then 2-4GB should be good.

Good Luck...

I did start in EFI mode. (I got the blackscreen asking me if I wanted to try Ubuntu or Install, etc) I will check out regarding that fast startup option. I have plenty of ram memory 8GB, and I haven't had problems that way before with Linux distros (unless I run something very intensive) but I think I will consider doing that anyway.

---

