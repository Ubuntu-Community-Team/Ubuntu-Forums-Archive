---
title: "gecko-mediaplayer &amp; Firefox"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-09-27
Unable to play stream from Firefox even though [FONT=Arial, Helvetica, sans-serif][SIZE=2]gecko-mediaplayer is installed - works aok on Chromium.

Also on another PC, same setup, and all is aok.

Any ideas?

have un-installed, re-installed etc etc no joy
[/SIZE][/FONT]

---

### Post by dino99 on 2011-09-27
it can be codec(s) missing (but remove gstreamer0.10-pitfdll as it breaks readings), or plugins security (FF addons)

.xsession-errors might tell you more :)

---

### Post by geidorei on 2011-09-27
Hi- thanks for info - gstreamer0.10-pitfdll not there, not listed on synaptic. removed gstreamer...ffmpeg - still woks on chrome, but still asking for plugin on firefox.

Error in .zsession-errors is:
** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/html decoder|decoder-text/html (text/html decoder)
** (<unknown>:2777): DEBUG: OpenStream reply
** (<unknown>:2777): DEBUG: 0x7f3ffee54110: "DestroyStream reason 0"
** (<unknown>:2777): DEBUG: 0x7f3ffee54110: "NewStream mimetype 'text/html' URL 'http://orange.citrus3.com:8022/'"
** (<unknown>:2777): DEBUG: 0x7f3ffee54110: "Not expecting a new stream; aborting stream"

Any suggestions???

---

### Post by dino99 on 2011-09-27
have you installed medibuntu repo ?

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal)

---

### Post by geidorei on 2011-09-27
hi - silly question, but why do i need to have those?

I have four other PC's and these repos have never been used, and the player on firefox just works on them - mixture of 11.04 and 10.10

---

### Post by geidorei on 2011-09-27
I lie lol!

medibuntu is already there is repo - but still no joy.

---

### Post by geidorei on 2011-09-27
Have also followed: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) - a bit out ofdate, but is what people keep referring too.

However, still cant get to stream music in Firefox - does anybody know how to resolve this issue?

---

### Post by lovinglinux on 2011-09-28
Looks like Totem plugin is still installed and taking over the content. Open the add-on manager by typing *about:addons* in the address bar, click the *Plugins* section and then disable all totem plugins.

---

