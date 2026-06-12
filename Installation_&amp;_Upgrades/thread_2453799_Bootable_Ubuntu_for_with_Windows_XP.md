---
title: "Bootable Ubuntu for with Windows XP"
date: 2020-11-17
forum: Installation &amp; Upgrades
---

### Post by yougotmi on 2020-11-17
Hi,

My current laptop is running on Windows XP and would like to download & use UBUNTU on bootable USB Drive.  What is the process to do so, as RUFUS requires Windows 7 & above to make a bootable USB Drive?

Also, let me know the process to download & install Ubuntu with multiple OS (Ubuntu & Windows XP)

Thanks,

Mohit

---

### Post by CelticWarrior on 2020-11-17
Welcome.

You may try [Balena Etcher]("https://www.balena.io/etcher/") or, if this also requires a newer Windows version, you can use the old method of burning a DVD.

You don't want multiple OSes if one of those is the hopelessly obsolete Windows XP. This Windows version has been out of support for many years. It's dangerous for you and everybody else if connected to the internet. DON'T USE IT, PERIOD.

And if you laptop is that old then the standard Ubuntu isn't recommended either. There are lighter alternatives like Lubuntu or Xubuntu. But if it's so old as to be 32-bit hardware then there are no good options currently. Please post your hardware specifications so we can take a look at it.

---

### Post by mastablasta on 2020-11-18
yumi, linuxliveUSB and unenbootin work on XP.

you need to create free disk space. but with windows xp the issue can also be that you don't have enough space at the start of disk to put grub there. on laptop it would be best to see which version /distribution works best using live session. test sound, networking (wi-fi), tocuhpad, printer, Fn keys and all that. then backup the data and install Linux over widnows XP.

otherwise the procedure is:
- create free disk space for linux
- make sure you have less than 4 primary partitions
- load live system and use free space for install or do manual install

---

### Post by guiverc on 2020-11-18
To download Ubuntu see [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
To download Ubuntu *flavors* go through [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

On a XP era machine, esp. laptop, I'd for sure consider a *flavor*. I can run Ubuntu fine (all releases) on some boxes that originally came with XP, however on other boxes I'd for sure **not** want to run main Ubuntu with GNOME (esp. the laptops). 

I saw mention in prior posts about testing first, for more details look at [https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)

To write the download ISO to thumb-drive, see

- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

You can write ISOs to thumb-drive on XP, as I've done it.  But I'd no longer look online for any such software for an XP machine (*too risky in my opinion*), so I'd write the ISO on another machine where software is easily available and less risky.

Yes if you have free disk space, the windows w2k & xp boot loader could be used to boot an ISO when written to a drive partition (ie. using the drive partition instead of a thumb-drive), but that wasn't easy to setup, and I'd not remember how that was achieved  (g*rub was easier to deal with and didn't require the use of a partition*)

As for using xp, I still have a system with xp on it.  Mine is not web  connected, but I do like two games that run on xp (*yeah at least one of  the games can be run on my GNU/Linux boxes too, but the game is buggy  & crashes a lot; when it crashes on Ubuntu I'm returned to my  desktop with a very low resolution display... when it crashes on xp I  don't care; I just power off*).

---

### Post by ActionParsnip on 2020-11-18
If all else fails you could get a friend to make the installation media for you. You can even buy install USB sticks on eBay

---

