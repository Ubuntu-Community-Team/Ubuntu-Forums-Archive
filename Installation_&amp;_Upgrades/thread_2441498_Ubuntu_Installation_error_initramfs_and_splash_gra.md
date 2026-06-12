---
title: "Ubuntu Installation error initramfs and splash graphics"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by sudiptarc on 2020-04-24
[COLOR=#242729][FONT=Arial]Trying to Following this post : [URL="https://askubuntu.com/questions/1210821/ubuntu-gtx-1660-corrupted-graphics"]https://askubuntu.com/questions/1210821/ubuntu-gtx-1660-corrupted-graphics
[/URL]
I'm new in Linux and have faced a problem for the last 5 days that's why I'm writing here.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When I'm trying to install Ubuntu on my PC its showing error like this[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][https://imgur.com/a/p5shpFj](https://imgur.com/a/p5shpFj)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I saw the Grub menu but don't see any advance mode. I have tried Shift / ESC no key working to go to advance mode.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I stuck here.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]PC Spec:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]i5 8400, Gigabyte b360m ds3h , 256GB SSD , Nvidia GTX 1660[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank You. :)[/FONT][/COLOR]

---

### Post by dino99 on 2020-04-24
Hi,
how have you made the installation ? If it is a fresh install the installer may have set the 440 driver required by your 1660 chip

[https://theitbros.com/install-nvidia-drivers-ubuntu/](https://theitbros.com/install-nvidia-drivers-ubuntu/)
[https://www.omgubuntu.co.uk/2020/04/things-to-do-after-installing-ubuntu](https://www.omgubuntu.co.uk/2020/04/things-to-do-after-installing-ubuntu)

---

### Post by sudiptarc on 2020-04-24
> **dino99 said:**
> Hi,
how have you made the installation ? If it is a fresh install the installer may have set the 440 driver required by your 1660 chip

[https://theitbros.com/install-nvidia-drivers-ubuntu/](https://theitbros.com/install-nvidia-drivers-ubuntu/)
[https://www.omgubuntu.co.uk/2020/04/things-to-do-after-installing-ubuntu](https://www.omgubuntu.co.uk/2020/04/things-to-do-after-installing-ubuntu)

Thank you for the reply. 

I haven't installed ubuntu. This is my first step, i just write the ISO with "balena Etcher" and trying to boot and this error coming. :(

---

### Post by CelticWarrior on 2020-04-24
You may need to use 'nomodeset' to run the live session and install. That is to be expected with some new Nvidia graphics. However, the error shown suggests a bad "burn". So, first of check the integrity of the downloaded ISO and if OK burn it again preferably in another USB stick.

---

