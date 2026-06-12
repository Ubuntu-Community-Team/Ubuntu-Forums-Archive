---
title: "Blank screen on restart after upgrades"
date: 2015-02-04
forum: Installation &amp; Upgrades
---

### Post by Michelle_Hughson on 2015-02-04
Hello, 

I am new to Ubuntu, and have been trying to learn quickly, but this morning after I installed some updates and restarted I am getting stuck on a black screen. 

When I restart, I see the BIOS screen, a purple screen (~5 sec), a long black screen (~15 sec), a purple Ubuntu loading screen (~1.5 sec), followed by the unresponsive black screen. The black screen lasts for at least an hour, so I don't think anything is ever going to happen if I just wait. 

I can still access my monitor's menu, so it is the computer not the monitor. 

I have tried reading up on solutions, and many places suggested accessing the GRUB menu (which I hadn't heard of until today). Anyway, I tried holding shift and the menu didn't show up, I also tried again while pressing shift repeatedly, same story.

Any tips would be greatly appreciated. 

Thanks.
Michelle

---

### Post by MAFoElffen on 2015-02-05
Welcome to Ubuntu Forums.

What make and model computer? Need info on the hardware (BIOS and Video) we are dealing with..

---

### Post by Michelle_Hughson on 2015-02-05
[COLOR=#000000]I am running Ubuntu 14.04 LTS. My system is a custom build: Asus M5A97 R2.0 motherboard, AMD FX6300 processor, and a MSI Geforce GTX760 graphics card. 

After some really hand wavy stuff I managed to get into my computer, but I don't think I solved the problem. I managed to find the GRUB menu through changing my boot drive in bios (I seem to have two identical drives to boot Ubuntu from in BIOS). GRUB menu, under "advanced options for ubuntu", showed that I had three "Ubuntu, with Linux x.xx.x-xx-generic" and three "[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-xx-generic (recovery mode)". I wish I had written down the numbers, but the last integer only differed by one in each set. 

eg. 
[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-x5-generic 
[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-x5-generic (recovery mode)
[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-x4-generic 
[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-x4-generic (recovery mode)
[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-x3-generic 
[/COLOR][COLOR=#000000]Ubuntu, with Linux x.xx.x-x3-generic (recovery mode)
[/COLOR][COLOR=#000000]
I opened the recovery mode of the largest number, and tried all the different clean-up, repair, etc options, and nothing worked. I then decided to try the second and third recovery modes. When I performed clean-up on those, I managed to get access to my computer (and everything seems normal). After the second recovery mode worked, I tested if the solution was permanent by restarting my computer, and I got the same blank screen. So I repeated the GRUB clean on the third recovery mode. At this point, I noticed the second recovery mode and it's non-recovery partner were gone. 

So cleaning the third recovery mode got me into my computer again, but I haven't restarted since until I have a few things to try. Or a the memory stick my friend lent me to originally install Ubuntu back for a re-install. 

I realize this is long winded and probably confusing, but hopefully it will help diagnose the problem. [/COLOR]

---

