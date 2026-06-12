---
title: "Plugin for AMSN with Beep Media Player"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by BrunoProg64 on 2006-08-22
Hello. I'm brand new in this forums. Well, my first question is: Exist any plug-in for Amsn that shows what are you listening in Beep Media Player?. I search personally but only found plugins for XMMS:( Suggest something please!!

---

### Post by Nightblade on 2006-08-24
They should work together? Aren't BMP and XMMS kinda the same thing?

---

### Post by nevermind85 on 2006-11-24
This is how i got it to work:

Go to the aMSN webpage and in the plugins section download the Music plugin. Copy that to your /home/<youruser>/.amsn/plugins folder (or to the shared one).
Remember to enable the plugin in the aMSN preferences.

Open up a terminal and install xmms-pipeinfo

```
sudo apt-get install xmms-pipeinfo
```

Now, go to /usr/lib/xmms/plugins/General and you'll see a libinfopipe.so there. Copy that (or move it or even better, symlink it) to your /home/<youruser>/.bmp/plugins/General folder.

Open BMP preferences, enable the plugin and you're ready to go!

---

