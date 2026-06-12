---
title: "didn't start after installation"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by xerasy on 2018-10-19
sry for my english

Installed Ubuntu latest version (18), the first time I installed it without connecting to the network, noticeable lag graphics shell (especially noticeable when watching video, video card I have GTX 1050 Ti). Execute the command
 ```
lspci -k | grep -EA2 'VGA|3D|Display'
```

result

```
01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1)    Subsystem: Gigabyte Technology Co., Ltd GP107 [GeForce GTX 1050 Ti]
    Kernel driver in use: nouveau
```

Decided to upgrade the drivers, as it is written here [https://help.ubuntu.ru/wiki/%D0%B4%D1%80%D0%B0%D0%B9%D0%B2%D0%B5%D1%80_%D0%B2%D0%B8%D0%B4%D0%B5%D0%BE%D0%BA%D0%B0%D1%80%D1%82_nvidia](https://help.ubuntu.ru/wiki/%D0%B4%D1%80%D0%B0%D0%B9%D0%B2%D0%B5%D1%80_%D0%B2%D0%B8%D0%B4%D0%B5%D0%BE%D0%BA%D0%B0%D1%80%D1%82_nvidia)

after reboot system appears black screen, even the grub is not shown, the expectation that will pass by itself, too, did not work. Reinstalled system, only this time was connected to a network, after installation all as the black screen (probably, at once downloaded actual drivers ). How i can to fix ?

---

### Post by pioneerio on 2018-10-19
upgrade nvidia drivers to 390 or 410.. the nvidia drivers that come with 18.10 break your installation and cause black screen.
follow these instructions: [https://askubuntu.com/questions/1033784/ubuntu-ugrade-17-10-to-18-04-nvidia-black-screen](https://askubuntu.com/questions/1033784/ubuntu-ugrade-17-10-to-18-04-nvidia-black-screen)

---

