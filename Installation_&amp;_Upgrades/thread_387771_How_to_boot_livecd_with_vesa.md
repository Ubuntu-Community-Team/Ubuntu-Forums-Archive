---
title: "How to boot livecd with vesa?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by MrNatewood on 2007-03-18
Hello,
I am installing Ubuntu for a friend who has a Voodoo 3 3000 graphics card. The LiveCD crashes when loading X. This is a known issue as I found on the ubuntu website.

The solution is said to be loading the Vesa driver instead of the tdfx, However it does not specify how to do that.
My question is how do I do that from the live CD?

---

### Post by msgmikeh on 2007-03-18
> **MrNatewood said:**
> Hello,
I am installing Ubuntu for a friend who has a Voodoo 3 3000 graphics card. The LiveCD crashes when loading X. This is a known issue as I found on the ubuntu website.

The solution is said to be loading the Vesa driver instead of the tdfx, However it does not specify how to do that.
My question is how do I do that from the live CD?

Here is some code that may help:

This is not my own, just copied and pasted from a thread that helped me.
[http://ubuntuforums.org/showthread.php?p=2276536](http://ubuntuforums.org/showthread.php?p=2276536)

press F6 at the first menu screen.
- delete "quiet-splash" and replace it with break=bottom
- Start the live CD, let stuff run and load, and then when the prompt appears, type

Code:

chroot /root nano /etc/X11/xorg.conf

- scroll down to one of the sections entitled "Device" that has your graphics card listed. Below it should be "Driver" and next to it "nv". This is the default nvidia driver on the Live CD, but apparently it has problems with our precious 7800 GTs. Replace "nv" with "vesa"

-then hit control + O
-hit enter
-and hit control + X

---

### Post by scxtt on 2007-03-18
have you tried "safe grafics mode"?

---

### Post by MrNatewood on 2007-03-18
> **msgmikeh said:**
> Here is some code that may help:

This is not my own, just copied and pasted from a thread that helped me.
[http://ubuntuforums.org/showthread.php?p=2276536](http://ubuntuforums.org/showthread.php?p=2276536)

press F6 at the first menu screen.
- delete "quiet-splash" and replace it with break=bottom
- Start the live CD, let stuff run and load, and then when the prompt appears, type

Code:

chroot /root nano /etc/X11/xorg.conf

- scroll down to one of the sections entitled "Device" that has your graphics card listed. Below it should be "Driver" and next to it "nv". This is the default nvidia driver on the Live CD, but apparently it has problems with our precious 7800 GTs. Replace "nv" with "vesa"

-then hit control + O
-hit enter
-and hit control + X

Thank you, however this did not help much.
After i press F6 the line ends with "quiet splash --" and not "quiet-splash", i tried replacing that with break=bottom(left the --- at the end), and after a lot of text processed i could enter the command, but there was no /etc/x11/xorg.conf file. nano opened a new empty file instead.

Safe graphics also did not help.

---

### Post by MrNatewood on 2007-03-18
Whoops, silly me. wrote x11 instead of X11

Works now :)

thank you :)

---

