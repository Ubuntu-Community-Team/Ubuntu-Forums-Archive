---
title: "Can't dual boot with windows"
date: 2018-09-19
forum: Installation &amp; Upgrades
---

### Post by loknath-dhar on 2018-09-19
I am new to Ubuntu, I tried to dual boot ubuntu with windows, create a USB to dual boot on my desktop PC. But It didn't install. It shows me error message can't install grub - something like this. I am sorry, I'm not sure. I tried twice.

I got SSD and HDD on my computer. Windows is installed in SSD as C drive and It didn't let me shrink more than 13GB. So, I made 50GB free space on HDD and tried to install Ubuntu there. It didn't work, said can't install grub.

and another thing, UEFI - I searched on google and learn something about this. I thought It would be better to install it on UEFI mode but when I tried, I saw a blank screen with ubuntu theme, nothing came along.

I tried to install ubuntu following the video tutorial from **Its foss** youtube channel. As there was an option, *install ubuntu alongside the windows*, I didn't see this option when I tried.

Can anyone help me out, what should I do?

---

### Post by oldfred on 2018-09-19
Is Windows UEFI or BIOS?
You want Ubuntu in same boot mode. And UEFI needs gpt partitioning.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yancek on 2018-09-20
You don't indicate which release of windows you are using so, guessing that it is 8 or 10, you might read the Ubuntu documentation at the link below which should explain a number of things.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by loknath-dhar on 2018-09-21
Thanks for replying. I replaced windows and installed ubuntu. I think this will be better for understanding computer, better.

---

