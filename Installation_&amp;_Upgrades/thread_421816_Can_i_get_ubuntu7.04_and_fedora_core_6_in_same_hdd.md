---
title: "Can i get ubuntu7.04 and fedora core 6 in same hdd?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by mytik on 2007-04-24
First of all, I everyone!
I got Ubuntu 7.04 (6.10 upgraded) in my laptop and i want to try fedora core before i can put it in my server, it's something like starting here in the laptop to gain experience then i will install it into other computers.
So, it is possible to install fedora core 6 in the same hard drive with ubuntu 7.04? I read that it could cause conflits by using the same swap partition :(  is that true?

Thanks, mytik.

---

### Post by Alekc on 2007-04-24
Ehm if you use different partitions for swapping files and swapping i dont think that there will be any problems

---

### Post by leg on 2007-04-24
You don't need different partitions for swapping but you will need different "/" partitions for each OS. I currently have fedora installed here but I don't like it much. Just partition your hard drive so that you have a spare partition to install it on and you will be fine.

---

### Post by mytik on 2007-04-24
:)  okay! One more thing, grub will automatically detect ubuntu partition? Once again, thanks!

mytik.

---

### Post by leg on 2007-04-24
Grub will sort itself out when you install Ubuntu. One thing you need to be wary of though is that my Feisty install insited on formatting the /boot partition. This means that if you have already installed Fedora you risk losing the kernel stored there. My suggestion would be to install Ubuntu first and then Fedora which (I think) allows you to skip formatting /boot & installing Grub. You will then need to add Fedora to menu.lst with something similar to this:
```

title Fedora Core (2.6.18-1.2798.fc6)
root (hd0,0)
kernel /vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/ rhgb quiet
initrd /initrd-2.6.18-1.2798.fc6.img

```Change whatever your system requires possibly the drive numbers. This came from my Fedora install.

---

### Post by mytik on 2007-04-24
I got ubuntu installed already. So installing fedora core in a nother / partition wil allow me to select what grub i want to use?

---

