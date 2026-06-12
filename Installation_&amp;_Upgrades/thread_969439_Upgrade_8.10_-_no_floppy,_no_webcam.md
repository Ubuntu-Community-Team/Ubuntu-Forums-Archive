---
title: "Upgrade 8.10 - no floppy, no webcam"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by lores on 2008-11-03
Hello.

I've just spent a few days trying to figure out how to get the new Ubu working. After I first upgraded from 8.04 per online-upgrade, I got my system totally destroyed. So, I fresh-installed it.

After these few days, two major problems I cannot seem to cope with are still remaining - in both installs (upgrade, fresh), I lost my floppy-drive detection (no /dev/fd0 nor gm-places entry) and additionally my webcam became non-functional (I've forgotten to check if it was detected after the upgrade, but on the fresh install it's not, which is the very issue).

Actually, I've two cams connected, a Z-Star (A4-Tech) and a Pixart (Labtec). Z-Star's always worked in Linux environments o-o-t-box, and Pixart I've never managed to even get detected* nor a /dev/video0 entry ascribed.

Now, it's Ubu 8.10... Z-Star does not even get detected* anymore, and Pixart gets a /dev/video0 entry, yet its signal (perhaps colour/format) is messed up and whenever I try to use it by an app, I either don't get it detected, or I get some random rubbish (sometimes with an error message).

* With no detection I mean the inability to recognise the device as a cam, as it obviously is listed in lsusb (the cam hardware is not a problem either).

As a result, after having upgraded to 8.10, I've not not only gotten some fancy new features, but pitifully also no cam and no floppy working anymore.

What should I do? :)

---

### Post by lores on 2008-11-04
Bump!

---

### Post by lores on 2008-11-05
ANYthing?

---

### Post by lores on 2008-11-08
Hey, it is quite a serious issue not to have the floppy drive available... Pls

---

### Post by loell on 2008-11-08
type 
```
sudo modprobe floppy
```

this will load the floppy module, check if your floppy device is detected.

---

### Post by lores on 2008-11-08
Yes! Thank You so much! That's all I've needed, now I have my floppy again! :D

*

I just wonder how come fd module is no longer loaded by default on floppy-equiped machines in Ibex...

---

### Post by loell on 2008-11-08
yeah, this has been reported on launchpad, that some machines doesn't load the floppy module.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651)

as pointed there, when you reboot your machine, it seems you'll gonna have to load it again? :( can you confirm that?

---

### Post by lores on 2008-11-08
Yeah, yet loading modules at boot-time ain't a problem, really (I suspect it's just adding the line "floppy" to one file :) ), but the problem is the default setting - one just does not get the fd-access, which is not really that good...

---

### Post by loell on 2008-11-08
what about your webcam? are you giving up on that one? ;)

---

### Post by lores on 2008-11-08
I don't really have a choice. Tried everything I could think of... :(

---

### Post by loell on 2008-11-08
> **lores said:**
> I don't really have a choice. Tried everything I could think of... :(

yeah, well, there's pretty much webcam detection regresion on intrepid and i bet this is also the case on other major distro. i guess try your luck on jaunty in the next five months.

---

### Post by lores on 2008-11-08
Yes... That's what remains after all, yet if things'll go the Intrepid-way, none of my cams is gonna not only function, but nor be recognised in 9.04... :)
I'm just hoping somebody'll have some clue as to what else I might try...

EDIT:
The Pixart-cam that's never worked before has started working. The quality is 10% of normal.

---

