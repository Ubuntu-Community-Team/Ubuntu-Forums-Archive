---
title: "Help me please!! Startup issue!"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by drewcoll on 2006-09-27
I just finished installing a dual boot of Win XP and Ubuntu on my IBM T22
900Mhz P3
256 Ram
40GB HD

Anyway, when I start grub and go to Ubuntu the startup screen finishes (the bar goes all the way across) and then I get some flickers and a black screen with first a flashing "_" and some cpu action, then the _ goes solid. This happened with the Live CD too, but I figgured with the full install it might not happen.

I used an alternate install cd, so its the laptop not the cds.

While tinkering, I went into the recovery mode, typed in "exit" and Ubuntu magically started up perfectly, but I'd like to be able to start it up directly from grub.

Edited!: I cant get into Ubuntu this way anymore, it just worked once... so tempting!

Any ideas?

---

### Post by gosh on 2006-09-27
You could try to open an other terminal (when you see the blinking cursor) with <ctrl><alt>F1.
Then login
And then try to start gdm (/etc/init.d/gdm restart)

If your Xserver fails you might be able to set this straight by 
sudo dpkg-reconfigure xserver-xorg
and follow the instructions

---

