---
title: "Stuck at a screen after installing Ubuntu Alongisde Win10"
date: 2019-09-01
forum: Installation &amp; Upgrades
---

### Post by zygoat2 on 2019-09-01
I have just bought a new laptop and i wnated to dual boot Ubuntu and Windows 10. So i left 170GB out of my HDD space for Ubuntu.
I used Etcher to make a bootable USB with 18.04LTS. 
After that, in the boot menu of my laptop, i made a new boot option in the menu, choosing the file "bootx64.efi". (Not sure if this was the wrong step. There was another "grub64.efi" in the menu also)
Then i booted through to ubuntu and selected the option to "Boot alongside Windows Boot Manager".
It installed then and told me to remove the USB and reboot.
But after selecting the Ubuntu option in the menu after booting, it was stuck at this screen with a blinking cursor. I have attached the image.
Please do help me solve this problem.
Thanks a lot in advance!

My laptop:
Asus TUF FX505Dy-BQ002T
Ryzen 3550H
Radeon RX 560X
1 TB Toshiba with Windows 10 as the other OS

---

### Post by pcfan1234 on 2019-09-05
Try booting with the boot option nomodeset, because it stucks at GPU detection.

---

