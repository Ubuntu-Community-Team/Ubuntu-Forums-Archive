---
title: "booting from USB doesn't work"
date: 2023-02-11
forum: Installation &amp; Upgrades
---

### Post by corkncat on 2023-02-11
I'm trying to install Ubuntu 22.04 on a Dell Inspiron 530 with a BIOS not UEFI. When I boot the USB at startup all I get on the screen is GRUB. I've left it like that for over half an hour thinking it was working on something but nothing changes. I've tried creating the USB with Rufus, Etcher and the default USB writer on Mint 21. Same results. I've even tried installing Ubuntu 20.04.5 and gotten the same problem. I get the same problem trying to install Mint 21 on the Dell although Mint 20 will install fine. 
There must be some way of getting Ubuntu 22.04 on the old Dell.

---

### Post by sudodus on 2023-02-11
0. Please tell us about the **graphics chip/card**: Is it built-in (in the CPU) or a separate card, for example nvidia? In that case, which version?

1. Check that the download was good: use **[FONT=Courier New]sha256sum[/FONT]**.

2. Try with [mkusb](https://help.ubuntu.com/community/mkusb). Since Etcher is a cloning tool, I think you can skip that option and try to make a live system by 'iso2usb' or some of the other options.

3. If I understand correctly, the computer is old and has a core2duo processor. You may have better luck with a light-weight community flavour: [Lubuntu, Ubuntu MATE or Xubuntu](https://releases.ubuntu.com).

---

### Post by corkncat on 2023-02-11
I figured it out! I found on an Ubuntu website that one of the causes could be an old BIOS. I installed a copy of Windows XP, downloaded a BIOS update (the latest was from 2009) from Dell and updated. I've been able to boot the USB and I'm now in the process of installing Ubuntu 22.04. Thank you for replying to my post
UPDATE: You are right* sudodus, *I ended up using Ubuntu Mate for a better experience.

---

