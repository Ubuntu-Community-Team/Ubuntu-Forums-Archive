---
title: "Rufus problem, what else can I use to burn iso to bootable USB"
date: 2020-05-20
forum: Installation &amp; Upgrades
---

### Post by stylis2 on 2020-05-20
Hi, I was trying to use Rufus last night to burn an ISO to USB and ran into an issue. Rufus was trying to download some additional files before burning. In the logs it showed that Rufus couldn’t download these files due to an Outdated SSL on the laptop(a really old Windows XP). The whole reason  I’m trying to use Ubuntu is to give this laptop a new lease of life so the kids can both home-school at the same time. Is there any other programmes that I can use to burn a bootable usb. I tried google and found ISO to USB but the computer didn’t recognise the usb when I tried to startup.

---

### Post by C.S.Cameron on 2020-05-20
UNetbootin has been around for quite a while and works well. 
[https://unetbootin.github.io/](https://unetbootin.github.io/)
Only problem is that persistence is limited to 4GB for casper-rw file (writable). 
If you need more persistence you can add a home-rw file for up to 4GB of data and settings.

If you need more persistence than that, it is easy to make a casper-rw partition by hand for unlimited persistence for Ubuntu 19.10 and later.

[https://askubuntu.com/questions/1126145/can-i-convert-a-live-ubuntu-usb-to-one-with-persistent-memory/1176695#1176695](https://askubuntu.com/questions/1126145/can-i-convert-a-live-ubuntu-usb-to-one-with-persistent-memory/1176695#1176695)

---

### Post by stylis2 on 2020-05-20
Perfect. This looks like what I’m after. Many thanks.

---

### Post by yancek on 2020-05-20
On a computer that old I would wonder if it is capable of booting from a usb.  Have you ever booted from a usb?  Might be better to use a DVD is you have a DVD drive.

---

### Post by stylis2 on 2020-05-20
Yes, I think it will. It was a while back but I remember doing the same to this laptop years ago before switching back to windows. Fingers crossed otherwise i will go and buy some blank cds.

---

### Post by oshman on 2020-05-20
> **stylis2 said:**
> Fingers crossed otherwise i will go and buy some blank cds.

You will need a blank DVD (not CD)

---

### Post by SeijiSensei on 2020-05-20
If you have a running Ubuntu installation, you can create a bootable USB device without Rufus.  You need one of the usb-creator packages, usb-creator-gtk or usb-creator-kde depending on what flavor of Ubuntu you are running.

---

### Post by C.S.Cameron on 2020-05-20
If you have a running Ubuntu installation, you can create a Persistent bootable USB device from scratch, no live USB program required:
[https://askubuntu.com/questions/1227221/simple-hand-made-persistent-usb-that-boots-either-bios-or-uefi](https://askubuntu.com/questions/1227221/simple-hand-made-persistent-usb-that-boots-either-bios-or-uefi)

---

