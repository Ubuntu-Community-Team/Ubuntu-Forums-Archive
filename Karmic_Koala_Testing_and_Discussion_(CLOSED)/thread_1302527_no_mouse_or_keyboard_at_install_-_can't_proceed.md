---
title: "no mouse or keyboard at install - can't proceed"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aaronp on 2009-10-27
Hi all,
I attempted to install Karmic RC today.
I got to the initial menu where you have the option to choose to boot the Live CD or install.
I choose install and almost immediately the light on my mouse (USB) goes off and my keyboard (PS/2) becomes unresponsive.

The process goes through the 'dimming' white Ubuntu symbol on a dark background for about 60 secs and then moves onto the first step of the install (asking me to choose a language) process.

At this point, I have no option but to do a hard reboot because my keyboard and mouse don't work.

I have successfully installed and run the Karmic RC in VirtualBox on this same PC, inside my current Hardy installation.

I can't find any existing bug that appears to be the same as this.

Any suggestions?

thanks
Aaron

---

### Post by aaronp on 2009-10-27
Hi again, I did a bit more reading and realised this problem needed me to specify apci=off and/or noapic before proceeding with the install.
I did this and I'm now on my way to being installed.

Anyone have any idea why these options are always required to be specified on my system?

---

