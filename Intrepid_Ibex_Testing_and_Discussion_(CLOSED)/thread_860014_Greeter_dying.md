---
title: "Greeter dying"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by joeinnes on 2008-07-15
On booting Intrepid Ibex, there seem to be no problems up until the greeter is started. Then, the stopwatch rotates for a turn or two, and hangs - although not completely. The mouse moves every minute or so, catching up to where it ought to be. If the mouse is moved before the screen hangs, then it hangs immediately. The only button that works is the power button (ctrl+backspace, switching to a different console, etc. all don't work).

However, if I boot into the previous kernel, I get a message along the lines of "Greeter application seems to be crashing" if I wait a while, and if I drop into a different console, I can run startx, which boots me into a fully working desktop. Any suggestions?

NB: Fedora 9 exhibits the same behaviour.

Also, if this is relevant, usplash and GDM default to a higher screen resolution than my screen supports. However, they did this in Hardy. I've still not fixed it, just let it run with the screen only showing the top left hand corner - when I log in, it changes back to 1024x768.

---

### Post by vikrant82 on 2008-07-15
I had a similar situation, However it was a temporary situation which got fixed with updates on 2 packages.

This has been discussed here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/245888](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/245888)

---

### Post by joeinnes on 2008-07-15
I've looked through the bug report, and it appears to be only intel cards that have been fixed for that situation. I'm also not convinced the problem is the same, although it does sound similar. I've updated to the latest xserver-xorg. Trying to perform the earlier fix is impossible (downgrading the mesa packages), because those packages do not have earlier versions in the repos. My graphics card is Via S3 UniChrome - but I believe I'm running the vesa driver. This means that I can't use compiz, so I should be using metacity.

---

### Post by vikrant82 on 2008-07-15
The older mesa packages wouldn't work with latest xserver-xorg-video-* anyways. (Although you can still get them from [here]("https://launchpad.net/ubuntu/intrepid"))

The bug is still open i.e. compiz or Kwin compositing doesnt work yet. However the greeter message issue was resolved after some updates.

Try enabling automatic logon by editing /etc/gdm/gdm.conf

---

### Post by joeinnes on 2008-07-15
Works with the 2.6.24-19 kernel, still the same problem with the 2.6.26-3.

Thanks for getting me this far though!

---

### Post by joeinnes on 2008-07-20
Interestingly, I've half solved the problem, by uninstalling compiz, and appending vga=315 to my kernel line.

315 is strange, because that's the 800x600x32 mode, but my computer boots quite happily in 1024x768x32.

Hopefully this problem will be solved fully before RC1.

---

### Post by kernco on 2008-07-26
I'm having this problem too on a laptop with a Via/S3 DeltaChrome IGP.  The laptop's native resolution is 1280x800, and this was detected and worked fine in Hardy.  In Intrepid, it defaults to using the vesa driver and 800x600 resolution.  If I edit xorg.conf to use the openchrome driver instead of vesa, the computer hard locks after a few seconds while gdm is starting (immediately after I hear the gdm startup sound), although it does correctly default to 1280x800.

---

