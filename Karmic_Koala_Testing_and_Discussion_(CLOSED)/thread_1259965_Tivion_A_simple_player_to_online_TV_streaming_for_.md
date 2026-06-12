---
title: "Tivion: A simple player to online TV streaming for Ubuntu"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shakaran on 2009-09-07
Hi, I am developing a *simple player* to online TV streaming for Ubuntu, my contribution is called "Tivion" (TV Online = TiViOn = Tivion), is a script based in Python, with a backend Mplayer and PyGTK. 

Actually it plays _36 british channels_, more than 30 spanish channels, 4 channels from Argentina, 5 spanish radios, and a russian channel!.

All this channels are free, and the public urls. My program is licensed on GPLv3

I am a Spanish user, but you can read more and download thanks to Google Translate (python source code for all OS, .deb for Debian/Ubuntu, Windows installer...maybe soon!).

[http://www.google.com/translate?hl=en&ie=UTF8&langpair=es%7Cen&u=http%3A%2F%2Fshakaran.es%2Fblog%2F2009%2F09%2Ftivion-0-0-2-ahora-con-48-canales-mas-mas-del-doble%2F](http://www.google.com/translate?hl=en&ie=UTF8&langpair=es%7Cen&u=http%3A%2F%2Fshakaran.es%2Fblog%2F2009%2F09%2Ftivion-0-0-2-ahora-con-48-canales-mas-mas-del-doble%2F)

**Launchpad Proyect & Code & PPA: **
[https://launchpad.net/tivion](https://launchpad.net/tivion)
[https://launchpad.net/~shakaran/+archive/ppa](https://launchpad.net/~shakaran/+archive/ppa)

The current version for now is **Tivion 0.0.2** and support 78 channels!

Regards and *happy testing!*

PS:You can *follow my blog* for new updates: [http://www.shakaran.es](http://www.shakaran.es) (on left menu you can translate my blog to your language).

---

### Post by MadsRH on 2009-09-07
This looks great :-D

I'm looking forward to more non spanish channels though ;-)

---

### Post by Eddie Hung on 2009-09-07
Hi! I would love to try this, but can you make it depend on gnome-mplayer or at least mplayer-nogui as well as mplayer -- assuming this will work? 
Trying to install your PPA pulls in mplayer which conflicts with these two packages.

Thanks!

Eddie

---

### Post by nperry on 2009-09-07
Don't know if its me, but i'm getting a audio sync issue, being about 2 seconds out on every channel (even LoSps)

---

### Post by shakaran on 2009-09-07
> **Eddie Hung said:**
> Hi! I would love to try this, but can you make it depend on gnome-mplayer or at least mplayer-nogui as well as mplayer -- assuming this will work? 
Trying to install your PPA pulls in mplayer which conflicts with these two packages.

Thanks!

Eddie

Done! You have a new .deb on my ppa now specifically for this issue ;)

> **nperry said:**
> Don't know if its me, but i'm getting a audio sync issue, being about 2 seconds out on every channel (even LoSps)

Open tivion with option -d o -debug, for example:
```
tivion -d
```

You see a message like:
```
Tivion 0.0.2
*** DEBUG ***
You can see additional output logs of Mplayer in /tmp/tivion-out-1252315290
...
```
You have a different /tmp/tivion-out-"some time number". Then play a channel for reproduce the audio problem and open the /tmp/tivion-out-"some time number".

If you get a error like:
```
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
```

Maybe you need use a different -ao (audio output) command.
You can see a full list running: 
```
mplayer -ao help
```

Then you can change -ao something (for default alsa) editing the file:
 sudo gedit /usr/share/tivion/tivion.py 

On line 683, you change -ao for other value (for example, pulse)

---

