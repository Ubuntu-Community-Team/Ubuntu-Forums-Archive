---
title: "Can I downgrade xorg to 10.04's xorg version?"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by STOIE on 2010-10-19
Hi there,

Having an issue getting any decent (more than 800px :P ) resolution or multi-mon action out of my Matrox M9148 card since I upgraded to 10.10
Is there any chance I can roll back to 10.04's version of xorg that the Matrox drivers are compatible with?

Help is greatly needed and appreciated.

Thanks all,
Aaron.

---

### Post by dino99 on 2010-10-19
have you removed or renamed xorg.conf ? if not, do it.

---

### Post by STOIE on 2010-10-19
Yeah I have, just results in crappy res on a single screen.

I can't get it to load with my xorg.conf it dies with "unable to load driver m9x"

---

### Post by STOIE on 2010-10-19
Okay, so I had a go at it myself.
Turns out it's just bluntly a bit of a bitch.

Downloaded the older debs for the previous version of xserver-xorg, xorg, xserver-xorg-core, xserver-xorg-graphics-all and xserver-xorg-input-all that were all shipped with lucid.

I uninstalled all of the versions on the box and reinstalled everything, turns out the installer whines that a newer version is available for the root package (ie. xserver-xorg-core) and you say yes, install the older one. But, then it happily blats over the older version of inputs you just installed with the latest it can find. I mean who wants the older version right!

Anyway, this kind of happened behind my back...
I rebooted thinking all ways well and guess what? It worked got a login screen, everything was nice, except ... just one thing... inputs... I had none.

Funny thing is when you have no inputs, you really can't do anything to fix it. CTRL+ALT+BACKSPACE doesn't work...

Anyway, before I mounted the system into single user mode, I remembered to try ssh, couldn't remember if I had enabled it (as it ships disabled), tested from my laptop and YAY! it worked.

Ran the dpkg uninstall on inputs and installed the old version, rebooted and now I type to you using the latest Gnome and Kernel, but, an older version of X.

It lives after all, learned my lesson now, I am going to wait until Matrox releases a new driver before I update again.

---

### Post by screwbunt2 on 2011-02-13
I found this thread: [http://ubuntuforums.org/showpost.php?p=10005160&postcount=7](http://ubuntuforums.org/showpost.php?p=10005160&postcount=7)

which has a more specific method to downgrade, although it is still missing a few details.

I'm in the process of trying to read between the lines and can't confirm that it works yet, but it might help someone.

---

