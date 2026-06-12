---
title: "Cannot reach desktop (&quot;Failed to load module &quot;fglrx&quot;) after upgrading"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by fredrikj on 2010-10-21
Hi all,

I just ran the Ubuntu upgrade manager and went along with the suggestion to do a distribution upgrade (to 10.10). Following this, when I start up my laptop, I only reach the command line (no Gnome session).

If I run "startx", I get:

...
Using system config directory "/usr/share/X11/xorg.conf.d"
dlopen: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: savedScreenInfo
(EE) Failed to load /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found
...

Any ideas what to do? The laptop in question is an ACER Aspire 5738ZG (graphics card Radeon HD4570).

Fredrik

---

### Post by fredrikj on 2010-10-21
I've tried replacing xorg.conf with xorg.conf.failsafe but this results either in a black screen, or a segfault message if I try to startx from recovery mode.

---

### Post by sikander3786 on 2010-10-21
Ubuntu no longer uses the xorg.conf. Try to reconfigure your graphics settings by,

```
cd /etc/X11
```

```
sudo cp xorg.conf xorg.conf.old
```

```
sudo rm xorg.conf
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by fredrikj on 2010-10-21
> **sikander3786 said:**
> Ubuntu no longer uses the xorg.conf. Try to reconfigure your graphics settings by,

```
cd /etc/X11
```

```
sudo cp xorg.conf xorg.conf.old
```

```
sudo rm xorg.conf
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Okay, I've done these. The result is that the screen flickers to purple as it usually does, but then I only get a black screen.

---

### Post by sikander3786 on 2010-10-21
You mean it is not automatically booting you to the command line any more, only the screen goes black? If so, it is a good sign.

---

### Post by fredrikj on 2010-10-21
> **sikander3786 said:**
> You mean it is not automatically booting you to the command line any more, only the screen goes black? If so, it is a good sign.

Yes. How is it a good sign? It's seems worse to me if I can't even get a command line to work with :-)

So what's the next step?

---

### Post by sikander3786 on 2010-10-21
If you don't see the Grub menu automatically, hold down and press the Shift key at your Bios screen. Now pointing to the first entry, press 'e' to edit it. Using arrow keys, navigate to "quiet & splash" delete them and type "nomodeset" in their place. Press Ctrl + X to continue booting.

Do you see the desktop now?

---

### Post by fredrikj on 2010-10-21
Nope. The screen flickers. It seems to turn on (purple light), then turns off with 1-second intervals.

---

### Post by sikander3786 on 2010-10-21
From the same Grub menu, you can select recovery mode and choose Safe Graphics Mode or something like that. Does that work either?

---

### Post by fredrikj on 2010-10-21
Nope, recovery mode with "failsafeX" gives an error message, including something about a Segmentation fault. The text disappears, so I can't reproduce it here unless it ends up in a log somewhere.

---

### Post by sikander3786 on 2010-10-21
I will be doing some search on that.

In the mean time you can start in recovery mode and choose to reconfigure X server or something like that.

---

### Post by fredrikj on 2010-10-21
How would I "choose to reconfigure X server"? That is apart from running xpkg-reconfigure xserver-xorg, which didn't help.

---

### Post by sikander3786 on 2010-10-21
> **fredrikj said:**
> How would I "choose to reconfigure X server"? That is apart from running xpkg-reconfigure xserver-xorg, which didn't help.
Retry ;-)

---

### Post by fredrikj on 2010-10-21
No luck again :(

---

### Post by sikander3786 on 2010-10-21
Try purgin fglrx.

```
sudo apt-get remove --purge fglrx
```

If it doesn't work, which graphics card have you got? Did you remove the proprietary drivers before upgrading to 10.10?

---

### Post by fredrikj on 2010-10-21
Ok, tried the purge, and that did the job.

THANK YOU! :D

So if I've understood correctly there is some incompatibility between the proprietary ATI drivers and Ubuntu 10.10, or perhaps something was broken about my installation (I haven't tinkered with it myself apart from installing upgrades, though).

The generic drivers should work fine -- all that was needed was to remove the broken ones properly. It wasn't entirely obvious how to accomplish this. Is there anything else I should know?

Thanks again for the swift help! This is why Ubuntu rocks, even when it breaks.

---

### Post by sikander3786 on 2010-10-21
You are Welcome! :-)

See this link for an explanation of the problem you encountered.

[http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

Happy Ubuntu-ing!

---

### Post by sutte on 2010-10-23
This solved my problem! Thank you!

---

### Post by neoragexxx on 2011-04-29
i solved mine by following the instructions on first page and reinstalling fglrx instead of removing .

---

### Post by Kladaradatsj on 2012-05-07
I had similar problems half a year ago when I had installed 11.10 on an HP Pavilion g series (they boiled down to a hardware problem solved by adding a HEX key somewhere and this problem, not so easily solved back then - I dislike AMD's APU's).

Today I updated to 12.04 (in-place) and again had the second problem (X failed to load module fglrx). For 12.04 however, I had to use the purge command. I also deleted the xorg.conf file (after another back-up). This made everything work just fine.

---

### Post by oldos2er on 2012-05-08
Old thread closed.

---

