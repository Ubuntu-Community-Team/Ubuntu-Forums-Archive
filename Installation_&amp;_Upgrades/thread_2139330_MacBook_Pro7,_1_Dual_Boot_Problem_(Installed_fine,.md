---
title: "MacBook Pro7, 1 Dual Boot Problem (Installed fine, cannot boot)"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by d3mncln3r on 2013-04-26
Hello, I realize there are a lot of topics like this, but I have parsed through many of them, but none of them have helped with the problem I'm having.

I followed the directions closely to dual boot Ubuntu alongside OS X. I installed rEFIt first, then Ubuntu 12.04 64-bit from a USB I made. Installation went fine, no errors.

rEFIt starts up and gives me 3 options to boot from: Grub, OSX and Legacy OS (which fails to load anything). OSX boots normally. Selecting Grub takes me to Grub. 

When I choose to boot ubuntu from grub, the splash screen comes up, then the screen completely dies and it just hangs.

I have tried to edit the Grub boot parameters (pressing 'e') to add different commands like "nomodeset xforcevesa; noapic; nointremap" according to various web sources I've found. None of these options work.

I'm not sure exactly what the problem is or where to go from here.

Thanks for any help, and please let me know if I left any information out.

EDIT:

[s]Ok, this problem is solved. When I first tried installing I opted not to create swap space for the install. Then I read somewhere that this can cause problems with installation. I wiped the partition clean, added 2GB of swap and reinstalled. This time everything worked fine... go figure. Now I have OSX and Ubuntu on my MacBook and I'm pretty happy.[/s]

EDIT 2:

I'd like to reopen this case because, this issue just occurred again. Even after Ubuntu worked for a few more boots. At one point during an Ubuntu session the OS booted up with very weird color problems (blocky 8-bit-ish type of malfunction). After this session, Ubuntu fell back into the same problem I explained above: the screen shuts off during boot, and everything seems to just stall.

Would love a little help/guidance, thanks!

---

