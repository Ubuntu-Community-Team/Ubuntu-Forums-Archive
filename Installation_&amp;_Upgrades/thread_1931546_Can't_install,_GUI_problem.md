---
title: "Can't install, GUI problem"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by vchris on 2012-02-25
I'm installing xubuntu 11.10 x86 on my home server. It was previously running win xp. It's an amd with close to 1gb of ram. I removed all the secondary drives. All I got now is a 40gb IDE HDD and an IDE cd rom.

Xubuntu installed properly but I'm not able to boot in the GUI. As soon as the GUI loading screen appears, the screens switches to terminal with the OKs and hangs at different places. Sometimes it's the bluetooth sometimes the next one after.

I figure maybe my install is bad so I select try Xubuntu without installing. Before getting to the GUI it switches to tty1. Same with Lubuntu 11.10 x86.

Hardware not supported?

---

### Post by josephmills on 2012-02-25
> **vchris said:**
> I'm installing xubuntu 11.10 x86 on my home server. It was previously running win xp. It's an amd with close to 1gb of ram. I removed all the secondary drives. All I got now is a 40gb IDE HDD and an IDE cd rom.

Xubuntu installed properly but I'm not able to boot in the GUI. As soon as the GUI loading screen appears, the screens switches to terminal with the OKs and hangs at different places. Sometimes it's the bluetooth sometimes the next one after.

I figure maybe my install is bad so I select try Xubuntu without installing. Before getting to the GUI it switches to tty1. Same with Lubuntu 11.10 x86.

Hardware not supported?

what about something like fluxbox or ICEWM ?

at server 
```
 sudo apt-get install icewm
```
then 
```
sudo update-alternatives --config  x-window-manager
```

pick IceWM then press enter. then try ```
startx
```
like I said there are alot options out there icewm fvm fluxbox openbox ect .

---

### Post by vchris on 2012-02-26
I got lubuntu 11.10 x86 going. I changed a parameter in the bios to use pci instead of agp.

---

