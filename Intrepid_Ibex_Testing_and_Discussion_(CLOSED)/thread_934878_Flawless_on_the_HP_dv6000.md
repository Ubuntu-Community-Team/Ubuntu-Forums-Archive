---
title: "Flawless on the HP dv6000"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SomeGuyDude on 2008-10-01
After trying a few Alphas, II has hit the point that it works flawlessly on my machine. Every little error that annoyed me with Hardy is fixed.

1) I can move my VLC window around and the video follow instead of sitting in its old spot until I stop dragging it.

2) Wireless LED works again.

A few other odds and ends.

Just so other HP dv6000 series users know, the alpha is ready to roll.

---

### Post by tim183 on 2008-10-01
which build are you using?

I#m running an hp dv6000 (actually dv6834eg)
it has an atheros ar5007eg wireless chip.

alpha 6 screws up big time, a constant sound at boot from the system beep.
think I'll try a fresh install for beta 1.

---

### Post by MJWitter on 2008-10-01
How did you get wireless to work? I have a DV6363eu and  it doesn't work by by default..

---

### Post by Perpetual on 2008-10-01
I have a DV6910US and as of 9/30 daily build Intrepid still does not work.  I have to hold down a key during boot or boot freezes.  Xserver refuses to start so I can not get to a graphical login.  Intrepid has so far been useless on this HP.

---

### Post by the real omni on 2008-10-01
I have a dv6500.

MOST of intrepid works for me, but there are a few issues that don't:

1) Wireless. For some reason the Broadcom hardware driver is deactivated every time I boot, so I have to manually activate it to get wireless up and running.

2) Avant Window Navigator. In Hardy, I was using the -trunk version and had no problems whatsoever, but in 8.10 there's a weird problem with icon drawing... Now and then (intermittently) the icon won't draw properly. Actually, the icon does draw properly, but it leave a grey vertical line between two icons now and then, as though the background isn't being drawn properly.

3) Power Management is busted completely. It's set to ask me what to do when I press the power button, but instead of bringing up a dialog with options, it just goes right into the shutdown routine and turns my system off. Also, it's set to turn the display off after 2 minutes but that never ever happens. (Worked properly in Hardy)

4) Clipboard Manager. Out and out broken. In Hardy I used glipper as a clipboard manager. Without it, if I copied something from a window then closed that window, the clipboard would empty before I could paste it in the target window. Now that I've updated to Intrepid, glipper crashes every time I boot up, because it depends on libffi4 but Intrepid uses libffi5. I've tried installing libffi4 but it has an unsatisfiable dependency with the version of gcc-4.2 used in Intrepid. I've also tried installing Parcellite, and it has no crashing issues - it just doesn't work. ;) Parcellite lists the clipboard history, but if I copy something in, say, Firefox, and then close firefox, the clipboard is emptied so I have to actually click on Parcellite and reload the entry into the clipboard.

---

### Post by the real omni on 2008-10-01
Oh and also, there's a weird issue with my keybindings for <SUPER>F, as illustrated in this post:

[http://ubuntuforums.org/showthread.php?t=934444](http://ubuntuforums.org/showthread.php?t=934444)

---

### Post by MJWitter on 2008-10-01
[Possible Broadcom Solution]("http://ubuntuforums.org/showthread.php?t=880218")
I used the method in the link and my wireless works now, although i have to type in the password for wireless network each time i restart.

---

