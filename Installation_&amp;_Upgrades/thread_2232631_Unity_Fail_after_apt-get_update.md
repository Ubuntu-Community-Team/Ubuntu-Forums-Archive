---
title: "Unity Fail after apt-get update"
date: 2014-07-03
forum: Installation &amp; Upgrades
---

### Post by matthewhrose on 2014-07-03
Hello,

Last night I ran a apt-get update/upgrade which installed several packages.  This morning however, I am unable to log in...as soon as I entered my password the system would freeze.  After some searching I have done an apt-get install --reinstall ubuntu-desktop, however that only now processes me to a blank background.  Going to CTRL+ALT+1 I can startx which does the same, but from there I can open a terminal.

I am very confused and not sure where to go with this one.  Thoughts?

Trying to start unity directly from terminal yields:

matt@matt-laptop:~$ unity
stop: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
start: Unknown job: unity-panel-service
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
libGL error: failed to load driver: i965
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell

(compiz:3516): GLib-GIO-ERROR **: Settings schema 'com.canonical.unity-greeter' does not contain a key named 'show-hostname'
Trace/breakpoint trap




Thanks,
Matt

---

### Post by bswarm2 on 2014-07-03
I also did the update last night and compiz is not starting, something broke on the update.

---

