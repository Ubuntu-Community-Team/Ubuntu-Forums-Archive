---
title: "Ubuntu freezes while in installer screen (Dual boot with Windows 10 - xps 15)"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by shivi9213 on 2018-10-03
Greeting, 

I have been trying to get Ubuntu to dual boot in my XPS 15 for a week now. The problem is that while installing it just freezes. I am able to move the mouse sometimes without any response. After sometimes even the mouse action will seize. Is there a problem or anything that I have to change with my graphics card? I can provide my laptop’s specs if needed

---

### Post by oldfred on 2018-10-04
Dell needs UEFI update from Dell and if SSD, the firmware for the SSD updated.
If nVidia card/chip, you need nomodeset for installer & first boot after install or until you install the nVidia proprietary driver from Ubuntu repository.
Drive(s) have to be changed from RAID or Intel SRT to AHCI. But install AHCI drivers into Windows first.

       Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en) 
    
General install instructions in link below in my signature.

---

