---
title: "Installation Unkown Error Ubuntu 24.01"
date: 2024-11-05
forum: Installation &amp; Upgrades
---

### Post by bongbowling on 2024-11-05
Hello,
I'm trying to install Ubuntu 24.01 but I'm constantly having the same error. It tracks to bootstrap subiquity server. I've tried downloading again the ISO image, flashing two different USB sticks. I've trying entering in graphics safe mode, disabling WiFi and Wired connections, and nothing has worked. My notebook is new, an HP Victus 15 with AMD Ryzen 5 and NVIDIA 3050. If someone has any clue or has the solution, please provide. [[size=1][color=#f8f8f8]geometry dash lite[/color][/size]](https://geometrydashlite.online)

---

### Post by oldfred on 2024-11-05
Must be that you are using a non-existing version.
There is no 24.01, current LTS version is 24.04.1. 

Generally the most current LTS version is recommended, but very new systems may need the current short term support version to have very latest kernel & driver or 24.10.

Does live installer in live mode work ok?
Better to leave Internet on. Wired almost always works. WiFi often works, but some need to download drivers.

What do you mean tracks to server?

Are you installing server or desktop version?
With nVidia you will need safe boot and during install choose to install optional restricted extras to get nVidia driver installed during install. You can install it later, but more difficult.
Are you creating installer in UEFI boot mode and booting in UEFI mode to install in UEFI mode.
Is UEFI Secure boot on or off? Should work either way, but sometimes Secure boot off works better.
Is this dual boot with Windows? Is Windows fast startup off, Bitlocker off. Many systems need drives set to AHCI, but some with just NVMe drive can use the Intel VMD driver with Intel RAID on.

---

