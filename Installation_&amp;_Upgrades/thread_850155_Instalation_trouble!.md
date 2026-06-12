---
title: "Instalation trouble!"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Gorgonkernel on 2008-07-05
First of all, i will like to congratulate all that are doing hard work for this operating sistem to be good. =D> Even if i am very begginer in the computer area i love what i see. 

I currently have a computer with Amd Sempron 2500+ processor, 512 Kingmax ram ddr 400, hdd 40gb Maxtor ata and Nvidia fx5200 video card. I tryed to install ubuntu 7.04. It works great but i need a driver for my video card. I tryed ```
sudo apt-get install nvidia-glx
```in the consol and it works. But after i restart the machine the screen goes black and i can not do anything. The bios works, it loads the operating sistem but then it goes black screen. What should i do? I have a 17" crt Horizon monitor for this machine. I tryed also ubuntu 8.04. I ordered it. But it freezes when i try to install it.
Can someone please tell me what to do?
Thanks very much!:oops:
Ps: If someone needs other information please tell me.

---

### Post by overdrank on 2008-07-05
> **Gorgonkernel said:**
> First of all, i will like to congratulate all that are doing hard work for this operating sistem to be good. =D> Even if i am very begginer in the computer area i love what i see. 

I currently have a computer with Amd Sempron 2500+ processor, 512 Kingmax ram ddr 400, hdd 40gb Maxtor ata and Nvidia fx5200 video card. I tryed to install ubuntu 7.04. It works great but i need a driver for my video card. I tryed ```
sudo apt-get install nvidia-glx
```in the consol and it works. But after i restart the machine the screen goes black and i can not do anything. The bios works, it loads the operating sistem but then it goes black screen. What should i do? I have a 17" crt Horizon monitor for this machine. I tryed also ubuntu 8.04. I ordered it. But it freezes when i try to install it.
Can someone please tell me what to do?
Thanks very much!:oops:
Ps: If someone needs other information please tell me.

HI and welcome, you may try to reconfigure your xorg with the command using the ctrl, alt, F1 keys at the same time and this will bring you to the command line and login
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or boot into recovery mode and use the xfix option.

---

### Post by Gorgonkernel on 2008-07-05
Xfix? What is that

---

### Post by avtolle on 2008-07-05
I don't know if that utility is available on 7.04 (xfix). Try the first command overdrank gave you in the post where he mentions xfix, and carefully answer the questions presented with reference to your graphics card and monitor.

---

### Post by Gorgonkernel on 2008-07-05
I upgraded to 8.04 and the upgrade was ok. I installed my driver finally but when i restarted the sistem. It loads to the user and password screen( i hear the sound in my speakers) but on the monitor it say OUT OF RANGE. Maybe i need a new monitor!:confused:

---

### Post by overdrank on 2008-07-06
> **Gorgonkernel said:**
> I upgraded to 8.04 and the upgrade was ok. I installed my driver finally but when i restarted the sistem. It loads to the user and password screen( i hear the sound in my speakers) but on the monitor it say OUT OF RANGE. Maybe i need a new monitor!:confused:

Ok if you hear the sound can use what I posted in #2 to try and configure you xorg?

---

