---
title: "Login resolution changes with any keystroke"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by kushko on 2007-05-08
Hi, I just installed Ubuntu 7.04 with the live CD.

When I booted off the CD it worked fine. If I try booting off the hard drive, everything seems to work fine.

But once it starts up and arrives at the login screen, any key I hit caused causes the screen to zoom in and then zoom out as I press the keys. It changes the resolution and refresh rate with each key press and doesn't register the keystroke in the username box. 

It cycles through resolutions from my default 1280 x 1024:
User Defined
User Defined
800x600
User Defined
User Defined
1024x768

Any ideas?

Kevin

---

### Post by joellord on 2008-06-21
Hi there !
  I have the same problem.  I have been using 8.04 for a while now and it works perfectly.  Now all of a sudden, when I get to the login screen, any keystroke changes the resolution of my login screen and doesn't type the letter...  therefore I can't login.  I have a lot of important things on that computer so any help would be REALLY appreciated !  Last thing I remember that I did was :

sudo apt-get install libsdl1.2debian-alsa

I was trying that because ZSNES wasn't playing any sounds.  Anyways, I started doing something else and I ran out of battery and the computer shut down.  When I restarted the computer, I had that keystroke problem.

Thanks,
Joel

---

### Post by unimatrix on 2008-06-26
Same problem here.

I installed the Logitech G15 drivers and everything worked fine, until I updated xorg (they released a 'fix' for this bug: [https://bugs.launchpad.net/ubuntu/hardy/+source/xorg/+bug/219630](https://bugs.launchpad.net/ubuntu/hardy/+source/xorg/+bug/219630) ).

I was also playing around with /usr/share/X11/XKeysymDB
I put it back the way it was, but it doesn't help.

Reconfiguring using dpkg-reconfigure xserver-xorg didn't work.

Also the effect is the same with USB and PS/2 keyboards.

Update: It's not a Login screen problem. I did a startx and it's happening in the window manager too.

---

### Post by unimatrix on 2008-06-26
Problem PARTIALLY SOLVED by adding
```
Option "CustomKeycodes" "on"
```
to /etc/X11/xorg.conf (Keyboard's InputDevice section)

All the basic keys now work, but I cannot seem to be able to use key combinations (like Ctrl+C or Ctrl+V), and also the extra keys don't work.

---

