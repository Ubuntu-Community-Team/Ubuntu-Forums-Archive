---
title: "system freeze"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Segi86 on 2012-12-02
Hi everybody, 
 
I`m having trouble with ubuntu installation, to be specific every time after booting my system freezes, the only thing I can do is  hard reset.  
I cleared my hdd (all of them)and when ubuntu live starts and the desktop loads everything freezes. I managed to install ubuntu before it boots from cd, but after the installation it still freezes after a minute.  
I`m trying to install a single system, the configuration worked fine with windows xp 
 
I tried these versions Ubuintu 12.10 32bit, 12.04 32bit, 12.10 64bit, 12.04.1 LTS 64bt, 11.04 32 bit. 
 
then i tried on Linux Mint 14.1 cinnamon 32bit 
the same problem occurs. 
 
I replaced my RAM, and the PSU still nothing  
 
this is my configuration: 
 
Amd Athlon 64 3000+ 
MBO dfi Infinity nF4X 
nvidia geForce 6600 
Kingmax 1GB DDR400 
Kingmax 512MB DDR400  
Crosair 512MB DDR400 
Seagate Baracuda 80 GB HDD 
WD 250 GB HDD 
WD caviar green 1 TB  
 
I did a memory test with Memtest86, and everything was fine  
I read on forums that I should update the kernel, but I can`t do that because everything freezes after less then a minute 
 
Please, please help I`m sweating over thins for a week now....

---

### Post by 2F4U on 2012-12-02
> I did a memory test with Memtest86, and everything was fine  

Did you let it run for at least two complete iterations? One iteration is often not enough to detect problems.

Is there any other hardware connected to the machine, besides keyboard, mouse and monitor?

---

### Post by ibjsb4 on 2012-12-02
Can you boot into low graphic mode?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+enter+low+graphic+mode+precise+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+enter+low+graphic+mode+precise+12.04&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Segi86 on 2012-12-02
> **2F4U said:**
> Did you let it run for at least two complete iterations? One iteration is often not enough to detect problems.

Is there any other hardware connected to the machine, besides keyboard, mouse and monitor?


It ran two iterations. 

line out is connected to my mixer, and a network cable to my modem  (I tried plugin in and out network cable, no effect )
that`s it..

---

### Post by Segi86 on 2012-12-02
> **ibjsb4 said:**
> Can you boot into low graphic mode?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+enter+low+graphic+mode+precise+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+enter+low+graphic+mode+precise+12.04&as_qdr=all&sa=Google+Search&lang=en)

Nope, just tried a couple of times :(

---

### Post by dino99 on 2012-12-02
which video driver is installed ? you should use "nouveau" with that 6600.

when you boot, edit the boot line to remove "quiet splash" to see if you get warnings/errors while booting.

have you tried booting in recovery mode ? (hold "shift" key down at bios end process to get the grub menu on a single OS system)

---

### Post by Segi86 on 2012-12-02
> **dino99 said:**
> which video driver is installed ? you should use "nouveau" with that 6600.

when you boot, edit the boot line to remove "quiet splash" to see if you get warnings/errors while booting.

have you tried booting in recovery mode ? (hold "shift" key down at bios end process to get the grub menu on a single OS system)

I removed the "quiet splash" and there was no errors.

I booted in recovery mode and started the dpkg, it uploaded the package but still no sucsess.

---

