---
title: "Adobe flash installation - &quot;Unknow channel natty-partner&quot;"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by robajz on 2011-11-27
Hi,

I've noticed recently, the flash player did not work anymore with youtube. It seems they require a newer version. Mine is Natty 64bit kubuntu. Trying the clicky way through the browser on the adobe website got me to the "Unknown channel natty-partner". Here's how I fixed it:

[LIST=1]
[*]Make sure you have the Partner repositories enabled.
[*]Uninstall flashplugin-installer
[*]Install adobe-flashplugin
[/LIST]

hth, gd, rob.

---

### Post by soulspit on 2012-01-17
Awesome, I had the exact same issue and ended up at Adobe's unhelpful page. I saw a bunch of other more complicated and unsuccessful solutions before finding this. Thanks for posting it!

**Edit:**
Actually, that didn't work for me, I was mistaken. I ended up having to download the .tar.gz source from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/), extract libflashplayer.so from it, and replace my old copies of libflashplayer.so with the new one. Found where the old plugin was stored with
```
locate libflashplayer.so
```
and for me it was /usr/lib/chromium-browser/plugins/ and /usr/lib/mozilla/plugins/ . Put the new libflashplayer.so in those directories and all was good. I'm on Natty Kubuntu.

---

