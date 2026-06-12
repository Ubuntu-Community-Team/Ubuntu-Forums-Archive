---
title: "errors uninstalling banshee"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Piaso on 2010-01-28
Hi.  I tried to install banshee on ubuntu remix through ubuntu software center and my computer froze, so i had to restart.  Banshee does not show up on the main menu, but is still partially installed in the system (it shows up on the apps list)  i've tried to uninstall it through ubuntu software center and terminal but continue to come up with this...

No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libbeagle1
 brasero
 libenca0
 libass3
 libcdaudio1
 libcelt0
 libdc1394-22
 libdca0
 libdirac0c2a
 libfaad0
 libiptcdata0
 libxml++2.6-2
 libffado1
 libfreebob0
 libjack0
 libkate1
 libmimic0
 libmms0
 libopenspc0
 libsoundtouch1c2
 libwildmidi0
 gstreamer0.10-plugins-bad
 libboo2.0-cil
 libmono-zeroconf1.0-cil
 libnotify0.4-cil
 libtaglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm very new to linux, and thanks for you help with this!

---

### Post by zvacet on 2010-01-29
Applications>accessories>terminal type

```
sudo dpkg --remove --force-remove-reinstreq banshee
```

---

