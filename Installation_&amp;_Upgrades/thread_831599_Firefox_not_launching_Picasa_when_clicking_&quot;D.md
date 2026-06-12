---
title: "Firefox not launching Picasa when clicking &quot;Download album&quot;"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by spraveenitpro on 2008-06-17
Hi 

There is an option to launch picasa from picasaweb site on firefox for downloading albums, upon clicking the link :
[B][COLOR="DarkRed"]
picasa://downloadfeed/?url=some URL[/COLOR][/B]

this should automatically launch picasa, now this does not happen,

the following settings are in about:config of firefox 3
[COLOR="Blue"][B]
network.protocol-handler.app.picasa;/opt/picasa/bin/picasa
network.protocol-handler.external.picasa;true[/B][/COLOR]

Pls let me know what can be done here.

Praveen

---

### Post by alexcuervo on 2008-08-04
BUMP

Running 8.04 64 bit, FF 3.0.1 and Picasa Linux 2.7 (Build 37.3615.0)
Download Link in picasa web album does nothing.

---

### Post by Myke Greywolf on 2008-09-02
I also have this problem. If I remember well, there's a workaround: copy the button link to the clipboard, open a terminal window, and write "picasa picasa://......", where the argument is the link you copied. I don't remember very well, and I'm not able to reproduce it right away, so this might not be 100% accurate. Try around.

It is annoying, though, and I don't understand why it happens.

---

