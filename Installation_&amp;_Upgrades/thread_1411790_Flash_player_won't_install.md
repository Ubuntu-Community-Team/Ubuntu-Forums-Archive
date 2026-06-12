---
title: "Flash player won't install"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by scott1541 on 2010-02-20
Hi Ubuntu forums people, it has been a while since i was last here, and also since i last used Ubuntu. I got a new laptop a few months ago with win7 and i since decided to install Ubuntu again. After attempting to install Ubuntu several times (2 actual, 2 wubi) i eventually got it installed thanks to my old friend the **Gnome Partition Editor**.

The problems i am having so far are that when i try to install adobe flash player with the .deb package it says 'Error: Wrong architecture 'i386'', I assume that this is because i am installing a 32 bit package on a 64bit OS, I also tried installing it via the APT option but that also didn't work, does anyone have a solution to this?

Also the wireless light flashes when there is Internet activity, this is quite annoying though i can live with it.

Running 9.10 64 bit

---

### Post by darkod on 2010-02-20
Are you after a player or just a plugin for firefox?
I had a problem with flash on 64bit ubuntu, and all I needed to do (after spending days on it) was download just the plugin, extract and copy it to:
~/.mozilla/plugins

I got it from post #3 from here:
[http://ubuntuforums.org/showthread.php?t=1306113](http://ubuntuforums.org/showthread.php?t=1306113)

---

### Post by scott1541 on 2010-02-20
Thanks, that totally worked, it took me a while to find the right folder but i eventually found it and made the plugins folder :)

---

### Post by bagata on 2010-02-21
Kako mozam da koristam Youtube i kako da go instaliram playerot??

Bi sakal da dobijam instrukcii na makedonski ili na croatian or serbian

---

### Post by darkod on 2010-02-21
Ova e samo za 64bit. Simni go fajlot sto e vo attachment, otpakuvaj go, i stavi go vo tvojot Home folder vo .mozilla/plugins. Ako folderot plugins ne raboti kreiraj go.

Folderot .mozilla ima tocka deka e skrien, koga ke go otvoris Home pritisni Ctrl + H da gi vidis skrienite folderi.

Izgasi go firefox i pusti go pak i imas 64bit flash plugin.

PS. Ne mozam da go stavam vo attachment, pregolem e. Odi na ovoj link i poglednit vo post broj 3, simni go od tamu:
[http://ubuntuforums.org/showthread.php?t=1306113](http://ubuntuforums.org/showthread.php?t=1306113)

---

