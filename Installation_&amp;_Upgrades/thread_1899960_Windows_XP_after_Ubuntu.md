---
title: "Windows XP after Ubuntu?"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by ?#Yhf%*&amp; on 2011-12-24
I recently got a Windows XP install disc, and I wanted to know how to dual-boot it on my netbook. I already have a USB disc drive, and I found [this article]("https://help.ubuntu.com/community/WindowsDualBoot").

My question is: how do I add Windows XP to my GRUB menu? Will GRUB detect the new OS automatically and allow me to dual-boot without configuration? If not, what would I need to add?

Thanks guys! :P

---

### Post by 2F4U on 2011-12-24
Are you installing Windows after Ubuntu on the same drive? If yes, there is an appropriate section with respect to the installation of Windows after Ubuntu in the article you mention. Windows will override GRUB and if you want it back, additional steps are necessary.

---

### Post by 73ckn797 on 2011-12-24
If you are able to boot to Ubuntu after installing Windows you can run in terminal ```
sudo update-grub
``` It will see Windows and add it to the Grub boot menu. Otherwise you would have to follow this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ?#Yhf%*&amp; on 2011-12-25
> **73ckn797 said:**
> If you are able to boot to Ubuntu after installing Windows you can run in terminal ```
sudo update-grub
``` It will see Windows and add it to the Grub boot menu. Otherwise you would have to follow this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks, that's what I was looking for :p Merry Christmas! :D

---

