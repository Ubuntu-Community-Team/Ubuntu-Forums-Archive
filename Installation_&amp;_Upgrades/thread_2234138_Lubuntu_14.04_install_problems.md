---
title: "Lubuntu 14.04 install problems"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2014-07-12
I installed onto a 10 yr vintage laptop which has Win xp Home on it.

All seemed to be going ok, it finished installing, and booted up, selected unbuntu and saw:

serious errors were found while checking the drive  for /.
press I to ignore , then
the disk drive for /tmp is not ready or not present


It asks for un and pw, after entry...
I get a command line: xx@ubuntu:~$

What gives?  Start over?

Thanks

---

### Post by Bucky Ball on 2014-07-12
*Thread moved to **Installation & Upgrades**.*

Nope. At that cursor, type:

```
startx
```

What happened?

---

### Post by ra7411 on 2014-07-12
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Nope. At that cursor, type:

```
startx
```
What happened?

I got more error messages- see attached pic of screen.
[ATTACH=CONFIG]254677[/ATTACH]

---

### Post by oldrocker99 on 2014-07-12
It would appear that your drive is toast. Try reinstalling and see if it works. If not, you may need to get a new drive, IF the laptop has SATA.

---

### Post by olli2 on 2014-07-12
The drive has both versions PASSWORDED & NEW: both versions work!

The only difference is that the new install doesn't detect WiFi builtin hardware.

I can still get WiFi with the first version.

So it is hard to know why that would indicate that the drive holding both working systems is toast?

---

### Post by Bucky Ball on 2014-07-13
Wasn't toast. I was about to chime in with the idea to remove Xauthority and ICEauthority, which appeared to be your problem, but a reinstall would have obliterated that.

Please mark this thread as solved and post a new thread for your wireless issue in ***Networking & Wireless*** to increase your chances of support as this is a new issue and has nothing to do with the original one. Feel free to post a link to the new thread here.

In your new thread, please provide the output of:

```
sudo lshw -C network
```

... to get things started. Good luck. ;)

---

