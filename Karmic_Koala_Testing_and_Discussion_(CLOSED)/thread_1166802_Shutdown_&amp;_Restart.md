---
title: "Shutdown &amp; Restart"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-05-22
This problem existed in Jaunty:

If I restart my laptop, Ubuntu shuts down but then just sits there with a black screen with a flashing cursor in the top left and doesn't restart. Ctrl-Alt-Delete does nothing so I have to do a hard power off.

I have a Dell Precision M90 laptop.

---

### Post by ranch hand on 2009-05-23
> 
Ctrl-Alt-Delete does nothing so I have to do a hard power off.

This has been disabled in Jaunty (jumpy jackass) and later.  This can be fixed;
```

sudo apt-get install dontzap && sudo dontzap -d

```
That should do it.  You want to look at your /etc/X11/xorg.conf file and makesure that it contains;
```

Section "ServerFlags"
    Option     "DontZap"    "false"
EndSection

```
You will need to reboot but then Ctrl-Alt-Delete should work.

This worked for my 9.10 (kinky kitten) installation too.

---

### Post by taavikko on 2009-05-23
> **ranch hand said:**
> This has been disabled in Jaunty (jumpy jackass) and later.  This can be fixed;


? Ctrl+alt+del is a different function than zap.
zap is used to "kill" Xserver nothing to do with shutdown.

phenest, does dmesg reveal anything?

---

### Post by ranch hand on 2009-05-23
Well. believe it or not, what this does is fix ctrl-alt-delete.

If you are using Jaunty you can try it and see for yourself.

---

### Post by sim-value on 2009-05-23
> **ranch hand said:**
> Well. believe it or not, what this does is fix ctrl-alt-delete.

If you are using Jaunty you can try it and see for yourself.

If Fixes Ctrl + alt + Backspace

---

### Post by ktp on 2009-05-23
> **ranch hand said:**
> Well. believe it or not, what this does is fix ctrl-alt-delete.

If you are using Jaunty you can try it and see for yourself.

[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

---

### Post by ranch hand on 2009-05-23
ktp
+1
I found it was better to "apt-get install" rather than just edit the file.  This did not seem to have anything to do with 9.10 but in 9.04-64 there woas a lib package removed.

---

### Post by phenest on 2009-05-24
Now I remember why this happened in Jaunty, and tested it in Karmic. If I disable the wireless, both shutdown & restart work perfectly.

---

### Post by taavikko on 2009-05-24
> **phenest said:**
> Now I remember why this happened in Jaunty, and tested it in Karmic. If I disable the wireless, both shutdown & restart work perfectly.

What was the driver/HW in question?

---

### Post by phenest on 2009-05-24
Intel 3945

---

### Post by taavikko on 2009-05-24
> **phenest said:**
> Intel 3945

Serious regression if that HW causes lockups...
iwlwifi driver is used by that? Have you found any related bugs?

---

### Post by phenest on 2009-05-24
I haven't looked for any related bugs, but this was an issue in Jaunty, and was fixed. I can't believe it's in Karmic too.

If there are no bugs reported, I'll raise one.

---

### Post by phenest on 2009-05-24
I can't find this bug reported on Launchpad. Under what package do I report it?

---

### Post by taavikko on 2009-05-24
> **phenest said:**
> I can't find this bug reported on Launchpad. Under what package do I report it?

AFAIK it should go against "linux" since it provides the driver.

"ubuntu-bug linux"

---

### Post by phenest on 2009-05-24
Reported: [bug #379976]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379976")

---

