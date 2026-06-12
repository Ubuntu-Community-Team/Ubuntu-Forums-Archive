---
title: "Upgrade total desaster"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Yumi on 2012-04-27
A "normal" upgrade from 11.10 with Gnome Desktop to 12.04 via update manager.

Result: Totaly unusable system. Windows have no closing or minimising buttons, Menus items can not be selected as they close as soon as the mouse arrow leaves the titel.

Running sudo apt-get -f install now it completely hangs a point refering to some kernel heading or something.

I can still open "previous versions" from Grub with the same result. Before the windows open, I can see some Unity icons. But they are invisable/inaccesable due to overlaying windows.

Just a warning to others. I go out to get a Ubuntu image burned to DVD and then reinstall.

Michael

---

### Post by josephmills on 2012-04-27
> **Yumi said:**
> A "normal" upgrade from 11.10 with Gnome Desktop to 12.04 via update manager.

Result: Totaly unusable system. Windows have no closing or minimising buttons, Menus items can not be selected as they close as soon as the mouse arrow leaves the titel.

Running sudo apt-get -f install now it completely hangs a point refering to some kernel heading or something.

I can still open "previous versions" from Grub with the same result. Before the windows open, I can see some Unity icons. But they are invisable/inaccesable due to overlaying windows.

Just a warning to others. I go out to get a Ubuntu image burned to DVD and then reinstall.

Michael

Yikes Michael sounds like you had some issues with compiz and window managing troubles. what is your vga card ? and what is your cpu ? and mem ?

---

### Post by finn on 2012-04-27
My wife's laptop suffered a similar fate, except the touchpad isn't recognised and wireless doesn't start (so I can't log in remotely to copy her files across).

As an added bonus while you can start programs you can't change the destination that the keyboard input goes to... it keeps going to the unity menu system which is now stuck behind the application that I just started.

Ctrl-Alt-F1 doesn't bring up a working terminal either (unless I hold down left shift during boot and select recovery).  When I do that still no network.

---

### Post by Yumi on 2012-04-27
AMD Radeon HD 6550M with 2643 MB Memory

Intel Core i5 CPU M480 2.67GHZ

Memory 4096 MB

---

### Post by rmayer32 on 2012-04-27
Those upgrades are hit and miss with every version it seems. I had it happen to me once and after that only clean installs. Hope you get it running.

---

### Post by Yumi on 2012-04-27
Back with a working desktop. I read in another thread about the login options.

Decided to try them all one by one. Selecting "Gnome Classic (no effects)" did the trick.

Michael

Edit: It did give me a sort of working environment back. But I had to remove unity by command line and in Gnome the top panel is missing which is very inconvenient. But at least I can now add and remove programs and change setting, working my way slowly through the mess the upgrade procedure caused.

Maybe it is time to consider a different Linux distribution.

---

