---
title: "&quot;Preparing machine to load &quot;Linux&quot;&quot; Dual-boot xp/linux"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Moldut on 2007-10-24
Hi

Yeah, the headline. Thats the message i get when i try to boot my fresh intallation of Ubuntu 7.10 Gutsy..

I started off with a Windows XP installation, I partioned my HDD into a swap section of 2 gb and a 30gb installation drive for linux, using Partition Magic. I install Boot Magic afterwards, boot from the Ubuntu cd and install without trouble on the drives created with Partition Magic. 
I restart, choose to enter the Linux partition from the Boot Magic selection screen, and it stucks on the message "Preparing machine to load "Linux"........

Im on an Acer Aspire 3100, no changed hardware, shouldn't be any problems.

Anyone got any tips? I'm pretty new to Linux, so I'd like some explanation whats going on ;)

---

### Post by logos34 on 2007-10-24
Use grub bootloader.  Boot from the ubuntu live cd and [install grub to mbr]("http://ubuntuforums.org/showthread.php?t=224351").

---

