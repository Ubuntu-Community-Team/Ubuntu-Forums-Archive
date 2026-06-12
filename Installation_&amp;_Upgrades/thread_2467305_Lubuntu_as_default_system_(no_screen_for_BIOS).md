---
title: "Lubuntu as default system (no screen for BIOS)"
date: 2021-09-22
forum: Installation &amp; Upgrades
---

### Post by celinemanekis on 2021-09-22
Hi,

Having already several computers running Ubuntu/Lubuntu, I am rather ok with the installation of Lubuntu alongside with Windows. But, today, I am stuck and would love the advice of the community! :P

I am trying to have Lubuntu alongside Windows 8.1 on a laptop with no native screen (broken a few years ago and completely removed), for which I use a VGA screen.
- Laptop is : HP Notebook 650 PC (2017)
- Runs Win 8.1 fine with display on external VGA
- I use my Live USB with Lubuntu 20.04 for the installation (have used it for other installation)

What I have done so far : 
- prepared and shrinked Windows : OK
- used the available space to install Lubuntu. Since it is EFI, it seems that I did not have to create a separate partition for boot)
- installed Lubuntu : everything went smoothly. No errors, it seems installed OK.

My issue is that it always start Windows. 
I have no screen until Windows is started, so : 
[LIST]
[*] I can not see the BIOS
[*]I can not see if Windows boot manager displays or not
[/LIST]

What I have done so far : 
- tried to force the BIOS to use my external display (so I could at least view something and work from there!). None of the tricks I came across worked to force the display on the VGA screen.
- ran grub-repair. There was a message mentioning that "Secure boot" was enabled. I forced the update of the BIOS and it seems to have disabled the secure mode.
- ran a second time grub-repair to get the report.

I paste here :
- the info I get from grub-repair : [https://paste.ubuntu.com/p/gy62jJy6nw/](https://paste.ubuntu.com/p/gy62jJy6nw/)
- the boot repair summary after running the recommended repair : [https://paste.ubuntu.com/p/NxxpMW3dX7/](https://paste.ubuntu.com/p/NxxpMW3dX7/)

I am reaching the limit of my knowledge on this topic and would like your help if possible.

What I would wish ideally : being able to choose between Lubuntu and Windows, with Lubuntu as default.

Thank you!

Céline

---

### Post by QIII on 2021-09-22
Duplicate of [https://ubuntuforums.org/showthread.php?t=2467306](https://ubuntuforums.org/showthread.php?t=2467306)

Closed.

---

