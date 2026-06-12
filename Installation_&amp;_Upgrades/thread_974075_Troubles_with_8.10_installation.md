---
title: "Troubles with 8.10 installation"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by citomaster on 2008-11-07
Hello,

Finally I made the switch from XP to Ubuntu on my old AMD system. But I'm having some troubles installing Ubuntu. I took the image of ubuntu.com and burned it properly on a dvd. As a test I installed it on my main system, and it worked perfectly. Now it was my older system's turn, but then I stumbled across a problem. When selecting "Install Ubuntu", you get the loading bar, and when it finishes I get to see the wallpaper, but nothing more. After a time the cursor freezes, and the only thing I can do is rebooting. I've already tried to select: NOAICP and NOLAPIC, but it still doesn't work. I also get the message that the firmware of my (Broadcom BCM43XX chip) wireless NIC should be updated, but that shouldn't cause the problem, should it? The system is running on a AMD Athlon 850mhz cpu, with an old MSI motherboard.

I hope you can help me sort this out,

Citomaster

*EDIT*

Amd Athlon 850mHz
MSI MS-(Will check up soon)
256mb DDR RAM
80GB IDE HDD
Nvidia geforce 2 MX400

---

### Post by Pumalite on 2008-11-07
Post your specs. Memory? Graphics?

---

### Post by dabl on 2008-11-07
"cursor freezes"

How about Alt-F1 or Ctrl-Alt-F1 at that point?  Do you get tty console?  It might be hanging on your graphic card. There are a lot of "vga=" boot cheatcodes -- you might want to try vga=791, for example, or vga=788, for lesser capable graphics cards.

[http://manual.sidux.com/en/cheatcodes-vga-en.htm#vga](http://manual.sidux.com/en/cheatcodes-vga-en.htm#vga)

Also, could the optical drive have an issue?  You might want to clean the lens and try it again.

---

### Post by Pumalite on 2008-11-07
With 256 MB of RAM you connot boot a Live CD; unless you make a 500 MB /swap partition ahead of time. I'd recommend you install XUbuntu.
256 MB of RAM or less>Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

### Post by citomaster on 2008-11-07
I'll download Xubuntu and try again, hope it'll work. Thanks for your help.

---

