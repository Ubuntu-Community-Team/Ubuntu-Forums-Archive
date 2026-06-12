---
title: "42&quot; Plasma Screen"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Mutha on 2008-01-31
Hi,

I have just tried installing 7.10 outputting to my plasma TV and After the Grub screen etc I just get a blank screen.

when I tried it off the disk it worked fine. I then installed and nothing.

It's going through a HDMI port from my Media Centre.

Any ideas.

Cheers,

M.

---

### Post by DrMega on 2008-01-31
I had this problem (not to such a good TV though). It seems that if you keep the 'SPLASH' option enable in menu.lst, then for some reason your TV out settings get ignored during boot up.

For me I took the 'SPLASH' option out of menu.lst. It means you get a text only boot sequence but at least it keeps your TV-out settings.

---

