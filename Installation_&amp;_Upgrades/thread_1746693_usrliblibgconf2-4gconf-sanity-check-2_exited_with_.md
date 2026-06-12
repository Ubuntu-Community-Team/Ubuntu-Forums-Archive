---
title: "/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by mahmoodkamal on 2011-05-02
I have installed 11.04 on an Acer Aspire 5336 to dual boot with Windoze 7. The installation went well and I reached the login screen of Natty.

Once i logged in I got a dialog box "[B]/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256". :confused:Once I clicked OK, the desktop appeared to go in some kind of a loop and nothing appeared, rather the cursor showed me it is busy.

I can still press, Ctrl-Alt-Del to get exit menu, but nothing else worked.

Can someone shed some light?[/B]

---

### Post by SonarSubs on 2011-05-02
Same problem. Upgraded 10.10 to 11.04. Wallpaper on desktop with same error above, but no icons or taskbars. Googled solutions but nothing works yet.

---

### Post by mahmoodkamal on 2011-05-03
i have found out this thread on Debian forum

[http://forums.debian.net/viewtopic.php?f=6&t=52862&p=304543&hilit=%2Fusr%2Flib%2Flibgconf2+4%2Fgconf+sanity+check+2#p304543](http://forums.debian.net/viewtopic.php?f=6&t=52862&p=304543&hilit=%2Fusr%2Flib%2Flibgconf2+4%2Fgconf+sanity+check+2#p304543)

will try out later.

The interesting part is Linux Mint is also giving the same error while PCLOS ran without even a small problem :-s

---

### Post by mahmoodkamal on 2011-05-08
I found out that the above directory did not exist on my PC.

I deleted the old partitions and installed again and this time it worked out. Apparently, last time when I did not wipe my old /home partition, some old files might have remained and must be creating conflict.

---

