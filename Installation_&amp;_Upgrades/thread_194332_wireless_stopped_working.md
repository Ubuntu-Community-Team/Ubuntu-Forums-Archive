---
title: "wireless stopped working"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by Baruch on 2006-06-11
I had Ubuntu  Breezy(5.10) installed on my PC. It recgonized my USR5416 PCI card and set it up automaticaly. I just did a clean install of Xubuntu 6.06, and I can't get it to recgonize my card. This happened both with the live CD and the alt. one.

---

### Post by llamakc on 2006-06-11
Do you see the card with the command `lspci -v` from the commandline (APPLICATIONS | ACCESSORIES | TERMINAL)?

---

### Post by smgil on 2006-06-11
[QUOTE=Baruch]I had Ubuntu  Breezy(5.10) installed on my PC. It recgonized my USR5416 PCI card and set it up automaticaly. I just did a clean install of Xubuntu 6.06, and I can't get it to recgonize my card. This happened both with the live CD and the alt. one.[/QUOTE]

With lsmod you can see if the wifi card module is loaded. I had same problem with an atheros card and with modprobe ath_pci I fixed it. Optionally, you can put the card module in /etc/modules for autoload on the module automatically on boot.

---

### Post by Baruch on 2006-06-19
Yes, I can see the card with lspci -v.


[QUOTE=smgil]With lsmod you can see if the wifi card module is loaded. I had same problem with an atheros card and with modprobe ath_pci I fixed it. Optionally, you can put the card module in /etc/modules for autoload on the module automatically on boot.[/QUOTE]
Sorry, that's too thecnical for me. What are these lsmod and modprobe things? How should I use them? (I know my card uses a Texas Instruments ACX 111 chipset, but I have no idea what exactly that means. Is that the module we're talking about?):confused: 


P.S. I tried doing a clean ubuntu Breezy install, and upgrading. On breezy the card worked fine, but after the update (which of course it managed to do over the internet using the wireless card), I rebooted when it told me to, and...:(

---

### Post by Baruch on 2006-06-30
sorry to bounce this back up, but it still isn't working

---

### Post by DreamWearl on 2007-01-10
I've got the same problem in 6.1 KUbuntu
got it to work after install, (same pci card)
and after update it disapeared...

whit  ```
lshw -C network
``` it's now markt als UNCLAIMED.

anybody?

---

