---
title: "Slugish Browser"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by godhika on 2009-08-12
I installed today alpha 3 and I am really pleased except for annoying little thing. Browser ( I tried it with Firefox 3.0 and 3.5, Chromium and Midori) are loading webpages very slow. Actually they load them very slow when the address differs significantly from the pages I have just opened, but they are very fast when the address is almost the same. 2 examples: from the karmic forum to, say, cnn.com ---> very slow. From the karmic forum overview to a thread (so only the last few digits in the address differ) it is amazingly fast. Tried the Futuremark Benchmarks for all these Browser and the results are the same or even better than under Jaunty. The download speeds are also just as usual. So it seems like all these browser just waste a lot of time resolving the web addresses. Has anyone an idea what could cause this behavior? I should perhaps mention its the 64 bit version with Gnome as display manager, the graphic card is an ATI HD 3450 (so a R600 chipset) with the opensource driver and no compiz.

---

### Post by matteo.gazzoni on 2009-08-12
I'm quite sure it's an issue with ipv6 dns lookups.

**Edit**: Try to type about:config in the Firefox adress bar, search for "ipv6" and set "network.dns.disableIPv6" to true.

---

### Post by psyke83 on 2009-08-12
[This]("https://bugs.launchpad.net/bugs/94940") bug is also a possibility (affects IP4 and IP6 connections alike).

---

### Post by godhika on 2009-08-12
> **matteo.gazzoni said:**
> Try to type about:config in the Firefox adress bar, search for "ipv6" and set "network.dns.disableIPv6" to true.

Guys you are great! This worked perfectly.Ok, Chromium is still much slower than I remembered it (15 seconds for Heise.de ???), but Firefox 3.5 is now fast as hell. Thanks a lot for the quick help.

Edit: I was a little bit too fast with my euphoria: It seems like there is still another problem. There are some websites which still seem to load extremely slow. For example the phoronix homepage takes around 90 seconds to load (Firefox 3.5 in this case)! So, once again, any ideas?

---

### Post by psyke83 on 2009-08-12
> **godhika said:**
> Guys you are great! This worked perfectly.Ok, Chromium is still much slower than I remembered it (15 seconds for Heise.de ???), but Firefox 3.5 is now fast as hell. Thanks a lot for the quick help.

Edit: I was a little bit too fast with my euphoria: It seems like there is still another problem. There are some websites which still seem to load extremely slow. For example the phoronix homepage takes around 90 seconds to load (Firefox 3.5 in this case)! So, once again, any ideas?

A website will respond fast if the DNS lookup is cached (due to a recent host lookup). For example, accessing Youtube for the first time will seem slow, but navigating to another link on Youtube should be fast (as you're accessing the same host).

Check the avahi bug and try the workaround by editing /etc/nsswitch.conf and changing:

```
hosts: files dns mdns4_minimal [NOTFOUND=return] mdns
```

To this:

```
hosts: files dns
```

Note: make a backup of the file before editing, and remember that this workaround will prevent Avahi from working correctly (but at least you'll know if it was Avahi causing the slowdown or not).

---

### Post by godhika on 2009-08-13
I should have mentioned that I already tried that workaround after you suggested that it could be this bug, but with no success. The first tip worked for Firefox, and it behaves like expect it to 95 % of the time, but other browsers ( I tried now Chromium, Opera, Arora and Midori) still are somewhere between slow and extremely slow. The problem seem to be random, sometimes it is obvious that it takes very long the resolve the host name, in other instances it is just loading the pages which is very slowly (I am are talking here about times of more than a minute).

---

### Post by matteo.gazzoni on 2009-08-13
You should report a bug.

---

### Post by godhika on 2009-08-20
Nevermind. i was away for a few days, and the newest updates fixed it

---

