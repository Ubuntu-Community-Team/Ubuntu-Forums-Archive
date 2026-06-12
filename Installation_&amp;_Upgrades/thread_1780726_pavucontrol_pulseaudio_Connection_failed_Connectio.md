---
title: "pavucontrol pulseaudio Connection failed: Connection refused"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by baumtopf on 2011-06-12
Hello ubuntu users,

I installed pavucontrol in Ubuntu Software Center again. If I start pavucontrol there is a error message like this:
"Connection failed: Connection refused". Does anyone know the solution of this problem?

A Screenshot is attached

---

### Post by baumtopf on 2011-06-12
Hello back,

I solved this problem. At first I uninstalled pavucontrol in Ubuntu Software Center. After that, I installed two packages from this side:

[http://wiki.ubuntuusers.de/pulseaudio](http://wiki.ubuntuusers.de/pulseaudio)

Install these,

maybe: apt://pulseaudio,pulseaudio-utils,gstreamer0.10-pulseaudio,libsdl1.2debian-pulseaudio
must, pavucontrol (universe): apt://pavucontrol

I'm not really sure, whether my way to solve this problem to solve your problem with this error message.
You can also watch my video:

[http://www.youtube.com/watch?v=qfAWW-hDJ3s](http://www.youtube.com/watch?v=qfAWW-hDJ3s)

Regards, Juergen

---

