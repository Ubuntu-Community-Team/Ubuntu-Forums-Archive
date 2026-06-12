---
title: "VNC4server gray screen"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by giruzz on 2007-11-06
Hi All,

I just upgraded my mum's PC and I use to connect using vnc4server...

After this upgrade I can't do it anymore. All I get is gray screen and a mouse icon that looks like an 'X'

I tried all the suggestions I found on various threads in this forum but none of them worked...and it appears I'm not the only one with this problem..

anyone can help?

thanks

g.

---

### Post by leonidas666 on 2007-11-06
I had the same problem. I followed this howto:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
and also there was only a grey screen with a X-Mousepointer.
Everything started working nicely when i used
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
 in the file Xvnc. (note the the "-extension XFIXES" at the end) instead of the original server_args.
This tip is mentioned somewhere in the howto, btw, it's just not too easy finding it in 13 pages...

---

