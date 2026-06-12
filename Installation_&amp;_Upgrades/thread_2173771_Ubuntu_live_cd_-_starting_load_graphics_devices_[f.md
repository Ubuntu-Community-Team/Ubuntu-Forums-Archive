---
title: "Ubuntu live cd - starting load graphics devices [fail]"
date: 2013-09-11
forum: Installation &amp; Upgrades
---

### Post by christhegoth on 2013-09-11
0 down vote favorite
	

I know I'm running old kit but Ubuntu used to be happy with that. Here's the problem.

AMD 64 single core processor. Onboard graphics. 756MB of RAM.

Used to be fine with Ubuntu 8.04. Updated 'live' ( no cd ) to 10.04 ( via the package manager ). Need to install from cd now and newer 12.10 cd won't be a good boy and load. I get the following error message:


starting load graphics devices [fail]


I have swapped out the data cable, dvd drive, and have now put in a second mobo ( same spec as listed above ).

An old spec that used to work fine now doesn't.

Is this a driver issue? I'm thinking it is as the older live cd's worked and these newer ones don't.

Any help would be much appreciated.

---

### Post by grahammechanical on 2013-09-11
The live session runs with the Nouveau open source driver. But this issue may be occuring before Nouveau is loaded. Do you see a purple screen? Or does this message appear before the loading gets that far? On the assumption that you see a purple screen with two icons at the bottom of the screen, I give you this.

1) At the first purple screen press Enter.
2) At the next screen select the language and press Enter
3) At the Try - Install text screen press F6
4) At the menu that appears bottom right select nomodeset and press Enter. That will put a tick mark against nomodeset.
5) Press ESC to get back to the Try - Install text screen.
6) Select Try Ubuntu.

You may need to experiment with some of the other F6 options, perhaps even using combinations of the options. This may be useful even if the error message appears after you have selected Try Ubuntu.

Regards.

---

### Post by christhegoth on 2013-09-11
I see the purple screen & can access all that.  But...

It's the graphics drivers that are failing to load.  When you click install the GUI fails to load.  You get the mouse, then it goes purple, then the graphics adapter shuts down and it then starts up again.  Mouse, purple, shut down.  And repeat.  For hours.

---

### Post by mörgæs on 2013-09-11
Double-posting is not welcome. Please stick to one thread, that is the one at Askubuntu.

Closed.

---

