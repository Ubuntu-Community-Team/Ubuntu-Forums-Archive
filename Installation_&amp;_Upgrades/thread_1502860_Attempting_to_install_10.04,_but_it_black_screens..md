---
title: "Attempting to install 10.04, but it black screens."
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by crazynovice on 2010-06-06
I am attempting to install Ubuntu 10.04 from a CD that is properly burned onto my sisters Toshiba Satellite A505-S6020 with an Intel i5, 4gb ram, and an NVIDIA GeForce 310M. The purple screen comes up that has the installation options comes up, but if I tell it to install the screen goes black after a short while of the cursor blinking up in the corner. It seems like it is doing something for a minute but then the CD stops spinning and it just sits there... My guess is that maybe its waiting for my input on how to install it but the display drivers aren't functioning properly... Does anyone know how I can fix this and get it installed?
By the way there are 2 partitions, one of them is empty and the other is an install of Windows 7 Home Premium if that has any bearing, on anything.

---

### Post by wojox on 2010-06-06
When you get to the options screen, ie. Boot without Chances, Install, Boot from Hard Drive. Press F6 and arrow down to *nomodeset* and select it by pressing spacebar.

---

### Post by crazynovice on 2010-06-06
Brilliant! Thanks. I knew it had to be something simple like that. I just didn't know what.

---

### Post by rampage355 on 2010-06-06
I get the same thing but even after i install, how do you get around the black screen when it goes black before the grub screen?

---

### Post by enaction on 2010-06-06
Sounds like I have a similar 64 AMD motherboard with Nvidia geForce card.  First graphics cut-out on install CD and had to use the "nomodeset" work-a-round. Then persistent problem with low graphics mode after grub.  No tweak on the grub worked for me.  The Nvidia geForce fix that finally worked for me was found here: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates).

---

### Post by rampage355 on 2010-06-06
could you explain the process you did.
If i install 10.4 from disk, reboot i have no luck with the video as i mentioned so how would I go about installing the x update?

---

