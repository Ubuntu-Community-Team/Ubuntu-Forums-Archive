---
title: "installed 2.6.11-1-686 and freezes"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by banditti on 2005-06-27
I apt-get'd linux-image-2.6.11-1-686 and I get to the login screen, but after I enter my password, it locks up.

I am on a IBM T40p

Thoughts?

---

### Post by Leif on 2005-06-27
Boot up to a safe session and go back to the 2.6.10 series. 11 is flaky.

---

### Post by skoal on 2005-06-27
I think I had some random lockups with this kernel as well. I use .12 and don't have those hangs anymore...
[list]
[*]add the 'noinotify' option to your kernel options in '/boot/grub/menu.lst', or...
[*]if that don't work, try using 'noapm' and 'noacpi' kernel switches at boot as well, or..
[*]try "NoAccell" = true or "RenderAccel" = false (or the like) in your xorg.conf.
[/list]

\\//_

---

### Post by banditti on 2005-06-27
How do I go to 12?

---

### Post by skoal on 2005-06-27
[QUOTE=banditti]How do I go to 12?[/QUOTE]
oooh...now there's a "hot" potatuh...

[here](http://www.ubuntuforums.org/showthread.php?t=43065&highlight=2.6.12) (warning! warning! danger will robinson! danger!)...or wait for "breezy" soon.

\\//_

---

### Post by Vorian on 2005-06-27
You should wait, 12 is not worth the headache!

---

### Post by skoal on 2005-06-27
Vorian!!!!! There just ain't enough good "reps" I can throw at you today!  I've been asking, no...pleading for some time now, "I gotta have more cowbells baby!".  And you, my friend, my gracious friend, have done just that!

+5 mod points for avatar!

I'll be watching you...

\\//_

---

### Post by Vorian on 2006-07-07
Yes!

---

