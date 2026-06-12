---
title: "Ubuntu upgraded from 10.04 &amp; problem with Media Player"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by mr.interested on 2010-10-12
Hello,

OK, so I've just upgraded my system to new Ubuntu, and unfortunately I can't watch films using Media Player. There's no sound, the image jumps, and the following two messages appear:

> An error occurred
Disconnected: Connection terminated> An error occurred
pa_stream_cork() failed: Connection terminatedI've tried several films that worked before the upgraded. They are in both AVI and MKV format. I've also reinstalled Media Player, but it didn't help.

I didn't install anything after upgrading the system. Checking the films was one of the first things I did. Also, I could watch them straight prior to upgrading the system.

Many thanks for suggestion and help.

Edit:

There are actually three errors:
> An error occurred
pa_stream_writable_size() failed: Connection terminated

---

### Post by andrewthomas on 2010-10-12
try to purge and reinstall 

```
sudo aptitude purge totem totem-plugins
```It couldn't hurt to remove the config files

```
rm -r ~/.gconf/apps/totem
``````
sudo aptitude update && sudo aptitude install totem totem-plugins
```

---

### Post by mr.interested on 2010-10-12
Many thanks for your replay. Unfortunately, the very same errors appear when trying to watch a film on Media Player. (VLC works fine though.)

---

### Post by Jetro on 2010-12-03
I get the exact same error as you, and nothing seems to work. Bumping for justice.

But you know what worked for me? It's not exactly a fix, but...

I use a USB soundcard as default. I set it back to the "original" default, that is, the laptop speakers, opened the file, and then I went into Sound Preferences and changed it again into what I like. No crash. ^_^

---

### Post by sabme on 2010-12-15
Same problem but Ubuntu 10.10.  AVI with AC3 audio has the problem another with MP3 audio doesn't.

---

### Post by pjalegria on 2010-12-15
remove gstremer0.10-pulseaudio solved

---

### Post by efflandt on 2010-12-15
I have not tried a 10.04 to 10.10 upgrade, but when I did a 9.10 to 10.04 upgrade, **ubuntu-restricted-extras** was no longer installed, and **flashplugin-installer** appeared to be the latest version, but did not show up in Firefox add-ons and did not work.  Installing the restricted extras still did not fix flash.  I had to mark flashplugin-installer for Reinstall before it worked.  So maybe installing or reinstalling those will help.

---

