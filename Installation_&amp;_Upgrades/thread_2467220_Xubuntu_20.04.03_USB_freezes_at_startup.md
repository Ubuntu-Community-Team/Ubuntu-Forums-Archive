---
title: "Xubuntu 20.04.03 USB freezes at startup"
date: 2021-09-19
forum: Installation &amp; Upgrades
---

### Post by matteo-dagord on 2021-09-19
Hi all,

I want to test the Xubuntu 20.04.3 on my Toshiba Satellite [FONT=Ubuntu]L50-b-24x, but the whole system freezes just after loading the graphical environment (wallpapers, icons...). I mean it doesn't react to inputs and the clock is frozen as well.
I tried rebooting several times.
As far as I understand, there aren't error messages while booting.
[/FONT]Currently I'm using Xubuntu 18.04 but in the past I installed both Mint 17 and Ubuntu 16.04, so I'm quite sure this isn't an hardware compatibility issue.
Any ideas?

---

### Post by MAFoElffen on 2021-09-19
Is it UEFI or Legacy Boot?

At the Grub menu, press <E>. Go down to the line that starts with "linux" and <Right-Arrow> over to where it says "quiet"... delete that word and replace with "nomodeset"... 

Press <Cntrl><X> to continue the boot process...

---

