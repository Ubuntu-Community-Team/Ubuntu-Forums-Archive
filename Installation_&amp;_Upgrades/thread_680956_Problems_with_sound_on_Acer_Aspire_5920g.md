---
title: "Problems with sound on Acer Aspire 5920g"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Arvidgp on 2008-01-28
Hello, I've just installed Ubuntu 7.10 on my Acer Aspire 5920G, but I'm having a problem with the sound, there are no sound at all. I have openen the sound manager by double clicking on it in the desktop, and set the volume to max, but it doesn't help. 
I'm new to Ubuntu, so it would be great with some help.

---

### Post by Arvidgp on 2008-01-28
I found a bit help on the german forum which helped me a lot, it does now allow me to connect my computer to my stero and play my music from it, but still I got no sound when I unplug it.
"1.) Konsole/Terminal öffnen
2.) Rootrechte besorgen: "sudo -s"
3.) Datei im Editor öffnen: "gedit /etc/modprobe.d/alsa-base"
4.) Als letzte Zeile in dieser Datei die Zeile "options snd-hda-intel model=acer" anfügen
5.) Datei speichern, Terminal schließen
6.) Synaptic starten: Paket "linux-backports-modules" installieren
7.) Neustart "
My german aint the best but I can try to translate it:
1) Open Terminal
2) Write in terminal: "sudo -s"
3) Then in editor open: "gedit /etc/modprobe.d/alsa-base"
4) After the last line here add this line "options snd-hda-intel model=acer)
5) Save the file.
6) Start Sypnatic: Install the package "linux-backsports-modules"
7) Reboot

I did this, and now sound is working using my stereo, I've put the volume to all devices volume to max, but still no sound. 
Thanks for any help.

---

