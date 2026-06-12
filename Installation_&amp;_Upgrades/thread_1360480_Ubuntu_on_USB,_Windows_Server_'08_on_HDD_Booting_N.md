---
title: "Ubuntu on USB, Windows Server '08 on HDD: Booting NTLDR before GRUB"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by FaNaTiX on 2009-12-20
Hi all,

I have Ubuntu installed on a USB flash drive and Windows Server '08 installed on a my hard disk. (Long story short, Win Server is used as a development and testing environment, don't hate me for using it as a workstation :P)

When I first boot the machine it loads up GRUB, which is the behavior I'm accustomed to and expected. However, because Ubuntu (and GRUB) is installed on a flash drive, it may not always be present when I boot the machine.

What would be the best course of action for me to be able to boot Windows when the flash drive isn't plugged in? Should I setup Window's NTLDR to prompt to choose between booting to Windows or Ubuntu? How should I go about setting everything up? I'm aware of setting up GRUB to boot into Windows, but I've never had to do the reverse, so I'm kinda clueless as to if it would even be the best course of action. On top of that I've always tried to stay away from toying around with GRUB after several incidents that are best left forgotten.

Thanks in advance. ;)

---

### Post by bboston7 on 2009-12-21
Instead of installing grub on the flash drive, I would install it on the internal hard drive.  From there, I would make Windows the default, but make a menu entry for the flash drive.

---

