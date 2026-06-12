---
title: "XP/Ubuntu Dual boot  (Ubuntu already Installed"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by Bre Ntt on 2011-06-30
Hello, I want to do an Ubuntu 10.04LTS and XP dual boot on two separate drives. I've done dual boots before but I have a unique problem I have to work around, as most tutorials assume one can install Windows first. I can't do that as I'll have some software registration issues (non-free software from school installed on Ubuntu). 

I've found a site with instructions a XP first, Ubuntu 9.04 second dual boot setup process, but it's clear from the very beginning of those instructions some of the steps are outdated as the GRUB files they say to backup aren't where they say they are. I might be able to figure it out with some thinking and deductions, but I'm likely to get myself into trouble if I have to stray to much from step by step instructions. 

Anyone know where I can find some relatively complete, relatively updated, instructions on how to go about this? 

Thank you, 
Bre

---

### Post by jerrrys on 2011-06-30
still seem to be dated, but so is xp...

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+add+xp&as_qdr=all&sa=Google+Search&lang=en#896](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+add+xp&as_qdr=all&sa=Google+Search&lang=en#896)

---

### Post by YesWeCan on 2011-06-30
> **Bre Ntt said:**
> Hello, I want to do an Ubuntu 10.04LTS and XP dual boot on two separate drives.

Hi. This is the easiest and best configuration, IMO. Put those tutorials away!

Simply disconnect you Windows disk.
Install Ubuntu on the new disk.
Reconnect the Windows disk
Set bios to boot off Ubuntu disk.
Boot Ubuntu
run sudo update-grub (adds XP to Grub boot menu)
Done.

---

