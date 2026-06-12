---
title: "Disappearing Mouse Cursor"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2016-04-25
hi:

i've upgraded a few systems to Lubuntu 16.04 (Thinpad X40), and everything works fine *except* the disappearing mouse cursor problem seen, apparently, with 15.04 and 15.10:

[http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update](http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update)

i've tried just about everything on the above page, including writing a pointer.sh script, no joy.  sudo service lightdm restart temporarily fixes it, but resets my desktop.

any ideas? 

if it's a bug that's being fixed, i'll happily continue on with my 14.04 systems and wait for the upgrade fix.

as always, you guys are the best!  thanks so much,

bill

---

### Post by sgarman on 2016-05-06
I'm hoping to find a permanent fix to this as well. I'm running xubuntu 16.04 on a Lenovo Thinkpad T450s. I only seem to lose my mouse cursor when waking from suspend. If I go to a virtual console (Ctrl-Alt-F1) and then back to Xorg (Ctrl-Alt-F7), I get my cursor back. Possibly a workaround you could use in the meantime without having to restart your desktop session.

---

### Post by wjbmd48 on 2016-05-06
On further research, this seems to be a pretty well-known bug in at least Lubuntu, Xbuntu, and Kbuntu, and a fix is supposedly in the works.  There's a simple and easy workaround: ctrl-alt-F1, followed by ctrl-alt-F7 cycles the screen off and on, returning the cursor; you don't even take your fingers off ctrl-alt to do this, very fast.  I'm a happy camper waiting for the permanent fix.        



Bill

---

