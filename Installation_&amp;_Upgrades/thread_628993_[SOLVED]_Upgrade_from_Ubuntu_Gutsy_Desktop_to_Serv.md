---
title: "[SOLVED] Upgrade from Ubuntu Gutsy Desktop to Server"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by plr4ever on 2007-12-01
I've been trying lately to get a server put together, and i finally decided on using on of my desktops that was running Gutsy beta. I updated it to gutsy final, and i downloaded the linux-server package. I'm not quite sure what it will take to get a server up and running, and i downloaded apache and mysql. I want to use the server to host some files, run a low-load webpage and hopefully a mail server. What packages would do this well, and are easy to use or learn? 

thanks everyone for your help, you've never failed me before!

---

### Post by IamAcoconut on 2007-12-06
I second that question. 

I installed a desktop Gutsy after failing to configure Internet connection in a headless Gutsy-Server. It turned out my modem was at fault and it wasn't a system/luser issue, so now I want to have a server version, but the box is headless (no display/keybord) and it must remain that way for a while, thus I can't perform a new install (even if I had time for that).

How can I make my box as (potentially) operational and secure(!) as the server version? Is there a (meta?)package for that, like "ubuntu-desktop", or "edubuntu-server"
It's already serving me as a router, but now I'd like to implement a few services.

P.S. Shouldn't this thread be in Server&Security?

---

### Post by zvacet on 2007-12-06
```
sudo tasksel install lamp-server
```

---

### Post by IamAcoconut on 2007-12-09
> **zvacet said:**
> ```
sudo tasksel install lamp-server
```
Hm, my tasksel hangs. Apparently after performing its tasks. The bluescreen saying for instance ```
uninstalling xyz: 100%
```
And it stays like that.
Last lines in the bash are:
```
Removing php5-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Use of uninitialized value in concatenation (.) or string at /usr/bin/tasksel line 369.
```
Should I be worried?

---

