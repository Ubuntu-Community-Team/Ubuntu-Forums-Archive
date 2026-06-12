---
title: "Volume control not starting"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by viraptor on 2009-10-17
Hi,
I've got a problem with the volume control applet / app after upgrading. Trying to restart pulseaudio via /etc/init.d/pulseaudio gives me only:

 * PulseAudio configured for per-user sessions

If I try to run either gnome-volume-control, or gnome-volume-control-applet, I get only:

 ** (gnome-volume-control:25716): WARNING **: Connection failed, reconnecting...

On the console and a similar message on in a dialog box after a while. System -> Preferences -> Sound gives the same result. I tried to force a dpkg-reconfigure on pulseaudio without any effects.

Sound itself works - even in typical "strange" applications like flash. There seems to be a pulseaudio daemon running too:

 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session

Help?

---

### Post by anders_c_ on 2009-10-18
the fault doesnt necessarily have to be pulseaudio, it can be the volume app itself, search for similar problems on launchpad and if there are none, file one.

---

### Post by dentaku65 on 2009-10-18
Try to delete or rename your pulseaudio settings
remove
```
sudo rm -R ~/.pulse
```
or rename
```
sudo mv ~/.pulse ~/.pulse.bak
```
and reboot your box

---

### Post by dentaku65 on 2009-10-18
> **anders_c_ said:**
> the fault doesnt necessarily have to be pulseaudio, it can be the volume app itself, search for similar problems on launchpad and if there are none, file one.

well... if pulseaudio is not installed or running the volume-applet does not even exist; to check:
```
ps -A |grep pulseaudio
```

---

