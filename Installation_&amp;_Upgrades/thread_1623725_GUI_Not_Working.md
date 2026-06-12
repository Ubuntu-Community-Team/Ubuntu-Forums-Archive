---
title: "GUI Not Working"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by younggolddar on 2010-11-16
I got a new laptop with Windows 7 64bit on it. Naturally, the first thing I did was try and dual-boot it with Ubuntu. I shrunk my partition and created some free space on the hard drive. I popped in my 10.10 disk and installed away. Unlike previous installers, there didn't seem to be a "use free space" option, so I specified my own (~3GB for swap, everything else (>100GB) for /). The installation seemed to go well, and then I restarted. To my surprise there was no fancy boot up screen, or even a GUI. I was greeted with a tty prompt.

Naturally, thinking I'd screwed up in defining the partitions, decided to use an older version of Ubuntu (10.04) which had the "use free space" option. I deleted the 10.10 partitions, and fixed the MBR, and tried again.

The install went fine, there was even a GUI (although the fancy boot screen, with the Ubuntu logo and the dots, didn't show up). It worked fine, so I performed a distro upgrade. A few hours later, I restarted my laptop to find... a tty terminal. I tried sudo aptitude install ubuntu-desktop, and turns out that I'd already had it installed.

What's wrong here, is it a driver problem or something completely different? My Windows version is 64 bit (it that has anything to do with anything). I have 3GB of (DDR3) RAM, a 1.86 GHz Intel Pentium P6000 processor, and an Intel GMA HD video card.

Is there even a solution to my dilemma, or am I stuck with an older version of Ubuntu/another distro (Mint maybe?)?

---

