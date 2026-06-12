---
title: "Karmic -&gt; Lucid: Hangs at Purple Splash Screen"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by linuxpyro on 2010-05-21
I was doing an upgrade on my desktop from 9.10 to 10.04.  The upgrade was going fine, but then suddenly froze.  (I tried to switch virtual desktops, must've been a bug somewhere...)  I restarted the machine, switched to a virtual terminal, and ran dpkg --configure -a to finish the upgrade.  This seemed to work without error, so I rebooted.

However, now the system doesn't boot up fully.  It will get to the splash screen with the five dots, which will continuously cycle, but it will not progress past that and give me a login.

Hitting the arrow keys I can't seem to find anything out of the ordinary; some services are started as they normally were (eg Apache and Cups), and the very last message is Checking battery state...  Which is [ OK ].

I can switch virtual terminals and log in from the console, and I can SSH in without a problem.  I've seen threads similar to this, but most of them seem to be relating to nVidia or ATI cards.  I have an nVidia card, but I'm not sure that's the problem.

Any ideas?

---

### Post by linuxpyro on 2010-05-21
Alright, I did some poking around and it seems that this isn't a Plymouth problem, this is a problem with GDM not starting.  I'm going to start a new thread in a more appropriate forum.

---

### Post by linuxpyro on 2010-05-21
Alright, all I had to do was reinstall GDM.  Here's my other thread for reference:
[http://ubuntuforums.org/showthread.php?p=9339265#post9339265]("http://ubuntuforums.org/showthread.php?p=9339265#post9339265")

---

