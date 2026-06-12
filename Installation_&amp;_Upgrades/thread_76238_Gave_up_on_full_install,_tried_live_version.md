---
title: "Gave up on full install, tried live version"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by ivanjs on 2005-10-14
If you read my previous post, the install goes beautifully (full version), but when it gets to where it plays the music and looks like it might be getting ready to log in, it always freezes.

Someone here suggested editing a conf file from the command line, but if I never even get into ubuntu, how do I call up the command line (I know Unix pretty well, and have been using the terminal for years, I just don't see how to get to the command line without being in ubuntu first, which is frozen).

Anyway, soI thought I'd try the live version-
Same problem. Right after hearing the music, I have a white cursor that moves around, but nothing-no login, no welcome, nothing.
Just sits there.

SYSTEM:

Gigabyte 8i915p board
Intel Pentium4 3.0 ghz 
200gig Maxtor ide drive
1 gig of RAM
CD and DVD burners
Windows XP (not that it matters for Ubuntu)
e-VGA 6200 graphics card 

The other guy suggested it's a 6200 problem, but again, I can't edit any conf files if it's frozen before I can get to command line.
Suggestions?

---

### Post by kvidell on 2005-10-14
Read my reply to your post, I just told you how to get to one.

Just do it _ before_ you try to login, while you're sitting at the login screen. Then login to the term.
- Kev

---

### Post by ivanjs on 2005-10-15
[QUOTE=kvidell]Read my reply to your post, I just told you how to get to one.

Just do it _ before_ you try to login, while you're sitting at the login screen. Then login to the term.
- Kev[/QUOTE]

thanks. I managed to get the xorg.conf file edited (had to chmod and sudo vi it-sorry, never used nano).

How, in the live version, do I get  back to the graphical login? I can't reboot, or the live version will reinstall/reinitialize everything, and the change I made to the xorg.conf won't stick.

I tried, exit, continue, etc.
Thx.

---

### Post by ivanjs on 2005-10-15
Ah, nevermind. I did a ps -aux | grep "X" and killed the process, which automatically restarted it for me.
Thx again
So live version works, now to try full version... :)

---

