---
title: "Way to go! Two upgrades in a row screw my machine!"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by justsee on 2007-04-11
Last time I updated (last week) I would try to login correctly, and it would login and boot me back to the login screen. That was fun, and ended up in me logging into terminal and re-installing my video driver for it to work again.

Today I updated to find the double-clock speed error for AMD 64 had returned. Turns out my /boot/grub/menu.lst files have been overwritten, and the additional parameters I had to add to fix the issue, things like noapci apci=off etc need to be added again. I've trawled the net and still can't remember the parameters required to fix the issue - has anyone else got this problem, and know the fix?

I also noticed things like my pc speaker returning - anyone know which upgrade has resulted in overwriting all these config files?

The Ubuntu upgrade process really is a major problem - I've had to fix broken wireless and a variety of other issues multiple times, to the extent that it's a major risk to ever update and reboot. Clearly not ready for the general public just yet.

---

### Post by justsee on 2007-04-11
Just for posterity: This was what I was looking for [http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed) . Though the fact I have to go through all this again after an update is still very crap!

---

