---
title: "Graphics failure after 9.10 upgrade"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aeriph on 2009-10-25
Today I upgraded from a totally functional 9.04 installation to 9.10. Upgrade seemed to go smoothly, but now the machine fails to boot after the initial Ubuntu splash (the new white one).

The monitor flickers between white lines and "out of range" errors and continues doing this indefinitely.

I can boot in recovery mode but dpkg and apt don't seem to be able to fix the problem automatically. It seems to be graphics-related. Does anyone know how to make it boot in low-graphics (low-res I think might help here) but not just command line?

Any other ideas would be appreciated.

---

### Post by munkifisht on 2009-10-25
I am having the same problem. it may be related to the ATI drivers. I have managed to get back to a safe mode, and then back to generic drivers using this method:;

[http://ubuntuforums.org/showthread.php?t=1300823](http://ubuntuforums.org/showthread.php?t=1300823)

---

### Post by Mark Phelps on 2009-10-25
There have been reported problems with ATI restricted drivers in Ubuntu 9.10.

If you're using ATI drivers, I would use the link below to remove them and replace them with the open source drivers -- for now.

Then when better drivers come out, you can install them.

ATI Radeon link:  [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by frisket on 2009-10-25
> **aeriph said:**
> Today I upgraded from a totally functional 9.04 installation to 9.10. Upgrade seemed to go smoothly, but now the machine fails to boot after the initial Ubuntu splash (the new white one).

I have a similar problem with the Live CD ... it gets as far as the top-line menus and then hangs the whole machine even in safe-graphics mode. Im assuming it's because it's an old Dell with an nVidia Geforce 4 card, but Ubuntu is failing to spot this and give me the 600x800 screen which would allow me to get in there and fix it. Any suggestions welcome...

[sunday] Just burned the Fedora 11 Live CD. I don't know what it is doing internally, but it works, and bring up X without blinking. If they can do it, why not Ubuntu?

---

### Post by Mark Phelps on 2009-10-26
> **frisket said:**
> I have a similar problem with the Live CD ... it gets as far as the top-line menus and then hangs the whole machine even in safe-graphics mode. 

Please do NOT hijack this thread for your problem.  It is NOT a similar problem.  Please start your own thread about problems using the LiveCD.

---

