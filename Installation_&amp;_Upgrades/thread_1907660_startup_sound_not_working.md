---
title: "startup sound not working"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2012-01-11
Hi,

I did two clean installs of Ubuntu 10.11, one on a Dell laptop and on a PC. Everything appears to work OK except for minor issue on the PC - cannot get the startup sound working.

Upon checking the config I noticed that the start up sound is played by canberra-gtk-play with the options of --id="desktop-login" --description="GNOME login" which works fine on the laptop but does not work on the PC.

Reinstalled canberra-gtk-play on the desktop without success. However, I can play the sound by running canberra-gtk-play with option --file=<path to sound file> which then plays the login sound. 

It appears that the login event is not recognized in the desktop installation for some reason.

Any idea  what could be the issue here? Of course, I am currently using the workaround of specifying the file pathname directly but would be nice not having to do this.

Thanks.

---

### Post by gdesilva on 2012-08-23
In case someone else is faced with this problem the solution is to copy sound files from /usr/share/sounds/ubuntu/stereo to /usr/share/sounds

---

### Post by gdesilva on 2012-09-07
And....if you want logout sound (and anything else to start at login or logout) check this out....

[http://ubuntuforums.org/showthread.php?t=1918649](http://ubuntuforums.org/showthread.php?t=1918649)

---

