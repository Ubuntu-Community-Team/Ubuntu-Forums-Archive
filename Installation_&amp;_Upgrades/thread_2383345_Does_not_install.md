---
title: "Does not install"
date: 2018-01-23
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2018-01-23
Good morning fellow ubunters (time here is 11:30 pm). I have heard it say that Windows systems do not like or let other OS install alongside them. I have unsuccessfully tried installing Lubuntu, Zorin, Ubuntu-MATE. I have tried installing some of them from a USB_ Rufus does not seem to help that much. I have tried installing in turns Ubuntu MATE and Zorin from a DVD, but each and every time, I get to the page where you choose the language and then the installation stops and I only get a black screen. 
Hardware : Fujitsu-Siemens Esprimo  E 5731 E star 5.0 with 7 Go RAM _ 64 bits. I bought this PC from "PlusdePc.com" (second hand) with Windows 7 already installed on it.

It proved far easier to install Ubuntu alongside Vista on my old HP dc 7700!!!

A trillion thanks to anyone who comes up with a solution to my problem.

---

### Post by oldfred on 2018-01-23
What video card/chip?
How much RAM? If 2GB or less then Lubuntu, Xubuntu or other lighter weight flavor may be better.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    
And most Windows 7 systems use all 4 primary partitions.
Post this from live installer in live mode.
sudo parted -l

---

### Post by christon74 on 2018-01-24
Hello Oldfred. I have said 7Gb RAM (Go= Gb). Motherboard is FUJUTSU D 3024 A1__ Processor: Dual Core Intel E5700 (2933 Mhz) __ BIOS: Phoenix__ Graphics board (video chip) : Intel Q43/Q45 (code name= Eaglelake_Q)

No UEFI. BIOS

---

### Post by christon74 on 2018-01-24
Solved! At long last I have finally installed a linux distro alongside windows 7, using UNetbootin. I have just installed DreamLinux 5.0.

---

