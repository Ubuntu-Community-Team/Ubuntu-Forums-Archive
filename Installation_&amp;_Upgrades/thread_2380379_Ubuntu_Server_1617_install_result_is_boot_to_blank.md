---
title: "Ubuntu Server 16/17 install result is boot to blank screen. Possibly UEFI related?"
date: 2017-12-16
forum: Installation &amp; Upgrades
---

### Post by mike689 on 2017-12-16
So I've tried installing the new Ubuntu Server 17 as well as 16.04 several times now and I cant seem to get it to work. Every time I install it I end up with it booting to a blank screen, not even grub.

I've tried doing grub-repair, and that fixes the grub menu but then it just boots to the same black screen with cursor. I've tried using the nomodeset flag at boot and that makes no change either.

I have a feeling it has something to do with a UEFI/legacy conflict with the system.

Right now I only have a 60GB SSD installed, and that's what I'm using to install Ubuntu 17 on. I've have scoured through every possible area of my bios and I cant find anywhere to set a distinction between UEFI and Legacy or turn off SecureBoot or anything like that. The system is a HP Compaq 8200 Elite Convertible. Imgur Galllery of all the BIOS menus that would potentially have any relevance: ([https://imgur.com/gallery/tAaGS](https://imgur.com/gallery/tAaGS))

I'm kind of at a loss of what to do at this point, I'm not sure what is preventing it from booting. Does anyone have any advise or insight into this issue for me?

Let me know if this is a topic that has been over posted (although I've done my fair bit of reasearch into, and have tried the majority of "fixes" for the issue to no avail. That's why I'm starting to think it's some UEFI conflict and I'm not sure what setting needs to be changed to fix it).

Thank you!

---

### Post by mike689 on 2017-12-16
Well, I happened to solve my own problem in a way I never would have expected.

I was using Universal USB Installer to make my USB boot device, but I kept noticing when it was asking where to install Ubuntu it was listing the USB device as sda1 and my actual SSD at sda2.

I decided to just say screw it and use unetbootin to make the USB device instead. Made it, it didn't show to the USB install process, and although it had an error trying to install any applications you want it to install during the installation, I didn't need them anyway so I skipped it. Installed, rebooted and it boots into the server just find.

Weird issue... but I guess for anyone else that may run into this: don't use Universal USB Installer!

---

### Post by mike689 on 2017-12-16
Actually, with unetbootin I ran into those couple errors trying to install things, and I'm having issue getting net-tools to install. It wants and ubuntu CD in the cd drive, and mounting the usb to the CD drive didn't seem to work.

So I used Rufus (as Ubuntu suggests and as I should have done in the first place if I'd been smart about it) and it worked flawlessly. No issues installing, no issues running. I still believe it was some sort of UEFI/Legacy conflict that Universal USB Installer was making somehow. Using rufus to format it for UEFI worked like a charm.

Use Rufus!

---

