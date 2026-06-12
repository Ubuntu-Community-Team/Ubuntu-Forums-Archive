---
title: "Pulseaudio Jack"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Shaythong on 2009-03-27
Hi I want to use Pulseaudio Jack so I can stream my desktop output directly with [http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack](http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack). When I run the .deb it says that the pulseaudio jack thing isn't installed. Any ideas?

---

### Post by markbuntu on 2009-03-27
You need to get the module-pulse-jack from the debian sid (unstable) repo. It works for me with pulse0.9.14
[http://packages.debian.org/unstable/sound/pulseaudio-module-jack](http://packages.debian.org/unstable/sound/pulseaudio-module-jack)

If you are using pulse 0.9.15 there is now a module in debian experimental

[http://packages.debian.org/experimental/pulseaudio-module-jack](http://packages.debian.org/experimental/pulseaudio-module-jack)

FYI You need to turn off system sounds or jack will not start and pulse crashes when you stop jack. Other than that is works very well.

It is not included in Ubuntu due to some really convoluted reasoning involving jack and freebob and ffado.

Pulse is still pretty unstable so you take your chances.

---

