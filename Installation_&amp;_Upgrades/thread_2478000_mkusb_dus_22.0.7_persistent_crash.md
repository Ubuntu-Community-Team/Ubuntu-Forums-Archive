---
title: "mkusb dus 22.0.7 persistent crash"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by etroniksargi on 2022-08-13
Hi SUs, I'm new in this forum and as a very longtime practicing electronic servicer  it's the first time I need help. 
The install of mkusb finished best with dus 22.0.7 - but by marking "persistent life" I got a "try and install"-USBl!!! And this more times and sticks on more testmachines. It seams the line persistens is chanched to install a try and install stick. 
My versions are: 
root@P8HTEST-PC:/home/wolfgang# mkusb -v
mkusb-dus:  dus 22.0.7
mkusb-plug: mkusb-plug 2.8.7
mkusb-nox:  mkusb-nox 11.1.9
mkusb-bas:  mkusb version 7.4.3
mkusb-11:   mkusb 11.2.2
My installation: 
mkUSB install auf USB-stick = 64 GB:                14.08.2022

cp UBUNTU_22.04.1_x64.ISO nach Ubuntu - home - download 

start UBUNTU_22.04.1 - Terminal 
- sudo -s 
- add-apt-repository ppa:mkusb/ppa 
- apt-get update 
- apt install --install-recommends mkusb mkusb-nox usb-pack-efi
- mkusb
- Eingabe: d = dus-Classic, easy to use - ok -> dus 22.0.7 - überschreibt alles! - ok 
- LMK auf 1. = 1 = wipe 1 (the first) Mibibyte - ok - selekt - ok - ja - Kontrolle - go 
  LMD auf 1. = i = Install (make a boot device) 
-               3. = p = Persistent live - only Debian and Ubuntu 
                2. = p = dus-persistent, classic dus method
- Dateimanager = Ubuntu-DVD-Abbild U22041.iso in home-downloads - ok 
- Anzeige USB-Stick = bei Übereinstimmung - ok - ja 
- Haken bei upefi - ok  
- Regler (für vfat-part) auf 50% (writable-part = min 20 GB!!!) - ok - warten  
- alt: 3x Warnmeldungen beantworten und ok 
- alt: Do you want to use grub.img - yes - ok
- Installation - bis Work done = ENDE - 2x quit - ok
Please tell me if I'm really wrong and where - or is it another reason?
My last mkusb stick run best on Ubuntu 20.04 with an older dus version. 
To all I send best wishes for a wonderful next weekend - so you have maximum time from todays monday morning to prepare you for enjoying 
from wolfgang

EDIT: 
Hi, after some tests with actually commands is following the same as on top:  
- /etc/apt/sources.list >>> inside: U22.04.1 Ubuntu + jammy 
- sudo apt-get update && sudo apt-get dist-upgrade 
- sudo add-apt-repository universe 
- sudo  apt update 
- sudo apt install mkusb >>>   dus 22.0.7 
I mean in dus is the link in the window  behind "persistent" really going to "try and install", but I'm not able  to control this. So now I'm rotating exponent 7 times around. 
Wish you all the best for ever from wolfgang 

EDIT2: 
Actually todays protokolls: 
1. dus 22.0.7 Final Checkpoint says:  Prepare persistent live system from ubuntu-22.04.1-desktop-amd64.iso to the target device /dev/sdb - go - yes 
2. with upper aktualysed USBstick the boot window presents:
- try or install Ubuntu
- Ubuntu (safe graphics)
- OEM install (for manufcturers)
- boot from next volume 
- UEFI Firmware Settings 
>>>>>   but there is no choise for persistent. 
Is any profi able to contact me please?

---

### Post by etroniksargi on 2022-08-14
~

---

