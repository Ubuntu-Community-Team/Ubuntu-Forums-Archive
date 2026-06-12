---
title: "Dual Boot Problems"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by zachery2 on 2015-03-28
I have an HP machine that came with windows 8 installed. I finally managed to get (partially) free of the cursed tyranny by dual booting ubuntu 14.04 (still need windows for certain programs). Then I tried to make a bootable usb for Tails OS as a throwaway computing stick. After attempting (and failing) to boot into tails, windows has once again claimed ownership of my computer. Ubuntu is still working fine, but grub no longer shows up and asks me what to load. Instead, I am now loading straight to windows just like I did before the dual OS setup. Tried Easy BCD, tried changing out of secure boot, tried grub customizer, tried playing with BIOS settings. I don't want to have to do an advanced restart from windows to use ubuntu!!

---

### Post by kc1di on 2015-03-28
Hello zachery2 and Welcome to Ubuntu,

Give Boot-Repair a try , it may fix the problem for you and if it does not it generates at file and stores it online. make sure you record the web page and past it here. 
you can get boot repair[ here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by zachery2 on 2015-03-30
Tried your suggestion. Worked perfectly, but I unfortunately missed the link. Based on what I saw while it was working, the solution was to reinstall GRUB. Thank you! :D

---

