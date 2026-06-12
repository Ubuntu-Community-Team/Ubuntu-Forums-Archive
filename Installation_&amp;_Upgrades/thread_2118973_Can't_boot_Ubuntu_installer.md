---
title: "Can't boot Ubuntu installer"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by L0rdLogan on 2013-02-22
I don't get why this is happening when windows is working fine,
I was running a Ubuntu 12.10 64 bit and was experiencing bugs, so i decided to downgrade to 12.04 LTS 32 or 64 bit.

When i attempt to boot it comes up with a kernel panic (Same kernel panic if i try to boot into 12.10 32/64 bit as well now 

Here is a picture of the kernel panic
[http://imageshack.us/a/img22/5734/20130221182210.jpg](http://imageshack.us/a/img22/5734/20130221182210.jpg)

I followed a suggestion by a forum member going by the name of: Jackhe22, which stated that my TV card was at fault because it was in my PCI slot, I took that out and tried again, same kernel panic,

PC specs: 
CPU: AMD phenom II X6 1090T BE (stock clock)
Mainboard: MSI 890FXA GD70
RAM: Corsair XMS3 (8GB DDR3)
Hard drives: 1 128GB Corsair Forcce 3 SSD (Unplugged during install), 1 60 Kingston SSD (Install drive), 1 Optima 2GB (Intall USB)
Monitors: 1 iiyama 1920x1080 plugged in via HDMI, 1 Acer 1280x1024 (plugged in via VGA (DVI to VGA adapter)
Graphics card: AMD Radeon HD 7950
Wifi card: Gigabyte GC-WB300D
TV card: DVB-T digital TV PCI card

Other USB devices e.g. Phones, Portable HDD's I didn't mention as they are not plugged in during the install.

Can someone please help?

---

### Post by oldfred on 2013-02-22
I have nVidia so I have not followed AMD. Some links to get you started.

       [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

    
       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by L0rdLogan on 2013-02-23
I'm sorry, But i fail to see how a video driver is going to help a kernel panic when i can't even boot into the installer! to install ubuntu

---

### Post by jackhe22 on 2013-02-23
The hexadecimal error that is being presented is mostly gibberish but partially translates to 'PCI', as well as strings before that error all pointing to something PCI related. Whatever it is, it IS hardware, not software. I told you to try and remove each PCI card until you boot, then replace them one by one to diagnose which it is.

---

### Post by L0rdLogan on 2013-02-24
Okay here is the Hex code converted into ASCII: ???|'????????S?????????????_32_????????????PCI??u????u???????

The '32' i believe is something to do with the latency timer on the PCI slot.

---

### Post by L0rdLogan on 2013-02-24
Bit of an update, I updated my bios successfully to the latest version V1.15 for my motherboard, Guess what OS I am running at the moment, That's right: Ubuntu 12.04 LTS.

Thank for your help guys, I'm glad this is solved and i do appreciate the help :)

SOVLED,

Idk how i change the prefix

---

