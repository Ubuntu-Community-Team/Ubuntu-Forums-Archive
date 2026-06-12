---
title: "Dual boot problems"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by jast1234 on 2010-01-26
I installed ubuntu 9.10 on my laptop previously. Later, I installed BackTrack 4 (final release) as a dual booting OS. The bootloader that BT4 installed detected and lists Ubuntu 9.10 in the boot list. However, when I try to boot Ubuntu 9.10, it gives me the error "Error 15: File not found       Press any key to continue...". I found this [article ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")but I'm not sure if it will work. Any advice would be appreciated.

---

### Post by hemimaniac on 2010-01-26
more then likely the grub is pointing to the wrong partition, i know in legacy grub one could hit the enter key, return to a dos menu, highlight the line in question hit "e" and change the (hd0,0) to (hd0,1) for example hit enter then "b" to boot to it and sort out the config file later, whether it works with the newer grub setups i don't know, I sadly gave up on 9.10 in 3 days because the sound problem list for my set-up was endless, yet it was handled in previous releases without incident.

---

### Post by jast1234 on 2010-01-27
Thanks for the help. Restoring GRUB 2 is apparently different than restoring the version of grub used in earlier versions of ubuntu. [This page]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") solved my problem for anyone else that uses 9.10 or later.

---

