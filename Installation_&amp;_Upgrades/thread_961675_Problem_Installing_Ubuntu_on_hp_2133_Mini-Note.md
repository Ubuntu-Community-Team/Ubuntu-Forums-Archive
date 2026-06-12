---
title: "Problem Installing Ubuntu on hp 2133 Mini-Note"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by tgamarques on 2008-10-28
HI, today I tried to install ubuntu 8.04 lts on my hp mini-note Kx872AA UK version, using a usb flash drive and after selecting install ubuntu in the first selection menu, it starts runing and appears a black screen of ubuntu with a loading bar and when the bar it's the end, when it's suppused to ask me about configurations and partitions of hdd the screens goes grey and I can't see anything I followed the steps provided by wiki ubuntu for this netbook and tryed 4 times with the same result.
Can someone tell me how to solve this??

Thanks

TGAMARQUES

---

### Post by Astinsan on 2008-10-29
boot in safe graphics mode. 
You are on a computer with a Via CPU and Video chip.

After you get the grub screen asking if you want to do a live disk / install etc.. there should be a button like f4 to select other options. Safe graphics. 

If it dies after the boot splash then X11 isn't starting because it doesn't detect the correct video chip. This will probably not be a issue after you get it installed.

---

### Post by michealk on 2008-10-31
You should be following these [HP 2133 installation instructions]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#How-To:%20%20Installing%20Ubuntu%208.04.1%20from%20CD%20on%20the%20HP%202133%20Mini-Note")

Specifically, you want to pass "xforcevesa" (no quotes) to the Linux kernel at boot-time. Do this at the boot menu by pressing F6 and typing xforcevesa. Then hit enter.

---

