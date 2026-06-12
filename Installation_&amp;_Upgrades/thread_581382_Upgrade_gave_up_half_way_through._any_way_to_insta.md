---
title: "Upgrade gave up half way through. any way to install what might have been missed?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Daminator on 2007-10-19
Hello all.

One machine upgraded fine. My main server machine had a whole host of problems relating to being unable to install Nvidia_glx and then gave up completely. Upon reboot I got a command prompt, then a low res gui.

I've used the latest version of envy to install the latest Nvidia drivers and have edited my xorg.conf back to how it was before the upgrade to give me the resolution I'm used to (setting up this projector was a nightmare a few months ago!), so I not have a system in some sort of working state. The problem is that I have no idea of knowing how much of the stuff that was supposed to be installed, upgraded, or removed actually got done. I'd guess about half to two thirds happened before it broke.

For example, I have the new background, but crappy cursor icons.

What can I do from here? Is there a way to install everything that should have been installed (maybe with the exception of whatever version of Nvidia drivers 7.10 wants to use by default as that's when the problems started). Any way to remove the stuff that should have been removed?

Cheers
Damian

---

### Post by Daminator on 2007-10-19
I know there are lots of people wanting help, but any advice on this?

Cheers
Damian

---

### Post by nach0 on 2007-10-19
try this command in a terminal:

sudo dpkg --configure -a

---

### Post by Daminator on 2007-10-19
Thanks for that. Unfortunately, it seemed to do nothing at all.

My system seems to be left in a state where there's a load of half installed system utils and eye candy and old apps that no longer work but haven't been fully removed.

---

### Post by Daminator on 2007-10-21
Can anyone help any more with this. I feel very uncomfortable with the half assed system I'm left with. I'll have to do a clean install if there's no way to do what 7.10 was trying to do from here.

Cheers
Damian

---

