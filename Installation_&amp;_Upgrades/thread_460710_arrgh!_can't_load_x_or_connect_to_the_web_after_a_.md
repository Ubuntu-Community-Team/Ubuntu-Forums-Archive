---
title: "arrgh! can't load x or connect to the web after a fresh feisty install"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by raul on 2007-05-31
Hi all

I seem to be one of the many unfortunate souls who have problems with ATI X*** graphics cards in Feisty. The original problem was that the liveCD wouldn't load. So I went with the alternative installation CD, following the suggestion in this thread:

 [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

The installation went just fine. The problem is that x doesn't load at all, and that I'm not connected to the internet to be able to follow the instructions in that thread. Any idea how can I connect to the web form the command line? I only have access to wireless connections... hope this doesn't make things worse. 

Thanks a bunch in advance.

---

### Post by frozinfire on 2007-05-31
When you say that x doesn't load, what do you mean? What happens instead?

---

### Post by raul on 2007-06-01
When I first start my computer, all seems to be going fine. Then I get a blue screen with the following:

```

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```

If I click ``yes", I get the following:

```

(==) Log file: ``/var/log.Xorg.0.log"
(==) Using config file: ``/etc/X11/xorg.conf"
```

Then I get:

```
The X server is now disabled. Restart GDM when it is configured correctly.
```

That takes me to the command line. If I put ``startx" there (after logging in), I get:

```

(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have usable configuration
```

This is, by the way, the very same thing I had been getting with the liveCD. A bunch of other people with ATI X*** cards have been having the same problem. The only solution I could find is the one I mentioned above.

On the other hand, from the command line I have access to everything. If I can find a way to connect to the web, I can try such a solution.

---

### Post by frozinfire on 2007-06-01
I have the Radeon x600 and had the same problem. If you enter
$ sudo dpkg-reconfigure xserver-xorg
what video card driver is chosen? I manually set mine to vesa, which fixed the problem, but yours seems to be different. You could try changing it, and hope for a little luck with trial and error.

Also, if you hit
$ ifconfig
is the wireless showing up?

---

### Post by raul on 2007-06-01
i tried vesa, but no results; yours works ok then? i don't know if part of the problem in my case is that i have 1900x1200 max resolution. but i doubt it: the same thing happens even if i rule out all high resolutions when going over dpkg-reconfigure xserver-xorg

yeah, i finally was able to connect to the web via iwconfig. but now when i enter sudo apt-get update, i get failed to fetch [http://.](http://.).. so i don't know what's up

---

### Post by frozinfire on 2007-06-01
Can you try skipping over the update part to $ sudo apt-get install xorg-driver-fglrx?

---

### Post by raul on 2007-06-01
I got:

```
Reading package lists... Done
Building dependency tree
REading state information.... Done
E:coulnd't find package xorg-driver-fglrx
```

I also edited my sources.list with nano (i.e. i  took the `#' symbols out of the `deb http' and `deb-src http' lines), but I get the same message.

---

### Post by anubhavrocks on 2007-06-01
Did you enable the universe and multiverse repositories?

---

### Post by frozinfire on 2007-06-01
Are you absolutely sure that you're connected to the internet? I think I read that the link signal can be deceiving; the computer sees the signal but isn't actually connected, usually because it's still trying to use the wired connection. Could you try $ sudo ifdown eth0 (or whatever your wired connection is called) and try the apt-get again? 

If that doesn't work, I always do this to connect:
$ sudo ifdown eth0
$ sudo ifdown wlan0 (my wireless)
$ sudo ifup wlan0
$ sudo iwconfig wlan0 essid linksys (my unsecured network)
$ sudo dhclient wlan0

---

### Post by raul on 2007-06-01
it seems i'm not connected indeed. when i ping [www.google.com](www.google.com) it returns unknown host. 

when i go for sudo ifdown eth0 (my  wired connection), i get ``interface eth0 not configured". what's weird is that  i get the same thing when i sudo ifdown eth1 (my wireless connection). so i don't know what's going on. eth1 (the wireless one) definitely seems to be connected: when run iwconfig alone, it verifies eth1 is connected to the right essid. that essid is also the only one that shows up when i type iwlist eth1 scanning.

any ideas?

---

### Post by raul on 2007-06-01
DONE! it's all working now... thanks guys. Will do a post on this tomorrow morning.

---

### Post by frozinfire on 2007-06-01
Great! No problem. :) Good luck with the video issue.

---

