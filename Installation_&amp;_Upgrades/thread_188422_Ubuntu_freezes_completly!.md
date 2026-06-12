---
title: "Ubuntu freezes completly!"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Sirkent on 2006-06-04
Hi and thanks for reading this!

Ok, this is a problem that also affected Breezy and which I hoped would be fixed in Dapper but obviously it isn't, so here I am. Debian (Sarge) has never had an issue on this hardware. If you're interested, my hardware is an Nvidia Nforce 4 motherboard with built in LAN, a Radeon X850XT, as well as an old sound blaster compatible sound card. So while that hardware is relatively new, it shouldn't be too uncommon.

It's safe to say that my hardware is reliable and free from trouble as I normally run Windows on this box and it's extremely stable.

This is a fresh install of Dapper. Quite simply, when gdm/gnome/x is running, my whole computer freezes up after a random amount of time - a matter of seconds, or a minute or two at best. This is a full freeze where the mouse and keyboard go and I can't kill X or switch to a different run level.

Everything appears to work before the freeze and I don't get any visual errors of any kind.

I also encountered this problem using the Live boot and had to use the alternative CD to install Ubuntu, however the freezing took considerably longer to occur when using the Live boot.

This doesn't occur if I go into 'recovery mode' and run gdm and login manually. When in recovery mode I have the fglrx module loaded and have even got glx and all the funky window effects running. For that reason, I'm relatively certain that my graphics configuration is OK. Sound and network also work flawlessly. Unfortunately that doesn't really narrow it down much.

I've had a look in the syslog for any errors or problems before the freezing and there's nothing. There is occasionally small patches of distortion on the screen, which points to a graphics problem. So maybe something is interfering with the graphics or conflicting with fglrx?

Unfortunately, with nothing in the logs I don't know of any way to get a lead on what is causing the problem.

What are the differences between running in recovery mode and normal mode?

What could be causing this issue or (more helpfully) how can I narrow this down?

---

### Post by Sirkent on 2006-06-04
This is the second time I've posted up this issue. Does nobody know anything about the differences between recovery and normal mode?

Surely there must be a way to track this down? It can't be too tough?

---

### Post by Lux Perpetua on 2006-06-04
There are known issues with fglrx and XGL. Other people have reported similar things. I also experienced freezes when I had XGL installed (a long time ago). This *may* help: [http://ubuntuforums.org/showthread.php?t=150854](http://ubuntuforums.org/showthread.php?t=150854).

---

