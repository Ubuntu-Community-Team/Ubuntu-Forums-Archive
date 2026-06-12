---
title: "Sound input not working after upgrading a bunch of pulse packages"
date: 2009-08-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-06
After doing an update I am not getting any sound from the built-in microphone. I played with Sound preferences, made sure "mute" was unchecked and I also tried in alsamixer increasing the mic boost and I tried out but internal and  mic. I went back to the Synaptic history and I noticed these were the packages updated. I am wondering if I should revert the update or if there is a way to configure things so the microphone works again:

```

indicator-applet (0.1.6-0ubuntu1) to 0.2.0~bzr319-0ubuntu4
libpulse-browse0 (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
libpulse-mainloop-glib0 (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
libpulse0 (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio-esound-compat (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio-module-bluetooth (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio-module-gconf (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio-module-x11 (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio-module-zeroconf (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
pulseaudio-utils (1:0.9.15-4ubuntu3) to 1:0.9.16~test4-0ubuntu1
vlc (1.0.0-1ubuntu1) to 1.0.1-1ubuntu1
vlc-nox (1.0.0-1ubuntu1) to 1.0.1-1ubuntu1

Installed the following packages:
libdvbpsi5 (0.1.6-1)
libindicate-gtk0 (0.2.0~bzr319-0ubuntu4)
libindicate2 (0.2.0~bzr319-0ubuntu4)
pulseaudio-module-udev (1:0.9.16~test4-0ubuntu1)


```

---

### Post by psyke83 on 2009-08-06
There's a thread [discussing the PulseAudio update]("http://ubuntuforums.org/showthread.php?t=1232342&page=2") already - [this]("http://ubuntuforums.org/showpost.php?p=7739984&postcount=17") comment should help.

---

### Post by andresmh on 2009-08-06
Thanks. I followed the instructions but unfortunatelly sound input is still not working.

---

### Post by miegiel on 2009-08-07
**kaitwospirit** and I are having this problem too [http://ubuntuforums.org/showthread.php?t=1233480](http://ubuntuforums.org/showthread.php?t=1233480)

---

### Post by andresmh on 2009-09-09
I updated Pulse Audio to the latest version and sound input is still not working. If you're also experiencing this problem, in particular if you have the same hardware 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Please help by adding more info to this bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819)

---

