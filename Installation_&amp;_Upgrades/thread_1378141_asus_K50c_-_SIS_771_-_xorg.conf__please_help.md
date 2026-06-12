---
title: "asus K50c - SIS 771 - xorg.conf  please help"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by hektor190 on 2010-01-11
I install Ubuntu 9.10 and drivers from this page: [http://pajky.blogspot.com/2009/04/sis-ubuntu-904.html?showComment=1263063965894_AIe9_BH3UovTOi_rR4GwWhziMYaMD1VLBdGFYeOD85DlchHAaj21eePUeoFEdj-j4dI6kjet41064Fy5aA65Z3PexPLMprMabVx_w65n1qq9kkVBYoJM6ZoIBW5zBjT3_WOOOI02blS7ZYkTYPnql0II3a1Vpc8h8JUtABpNKB5JKa2kWEby8P1ssp3qPFn1AVNeMdImkPMLd230MjOzBpGLHEcNLO3K-Q#c5396565985966032946](http://pajky.blogspot.com/2009/04/sis-ubuntu-904.html?showComment=1263063965894_AIe9_BH3UovTOi_rR4GwWhziMYaMD1VLBdGFYeOD85DlchHAaj21eePUeoFEdj-j4dI6kjet41064Fy5aA65Z3PexPLMprMabVx_w65n1qq9kkVBYoJM6ZoIBW5zBjT3_WOOOI02blS7ZYkTYPnql0II3a1Vpc8h8JUtABpNKB5JKa2kWEby8P1ssp3qPFn1AVNeMdImkPMLd230MjOzBpGLHEcNLO3K-Q#c5396565985966032946) 

Link to driver:
[http://www.mediafire.com/?yjjnjxmyzj9](http://www.mediafire.com/?yjjnjxmyzj9)

Installation is ok but computer have 1366 x768 px resolution how create good xorg.conf for this laptop?

Graphic without xorg.conf doesn't work. I can see some lines - that's all


// sory for my English

---

### Post by hektor190 on 2010-01-11
```
sylwia@sylwia-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
sylwia@sylwia-laptop:~$ 
```


Anybody?!?   - i should install Windows?!?

---

### Post by Zarok on 2010-01-29
I also have this same exact problem - if someone could help I'd greatly appreciate it!

---

