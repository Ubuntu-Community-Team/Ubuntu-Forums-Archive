---
title: "Weird installation issues"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Xeeon on 2007-10-30
this is very very odd for me...

I used to have Fedora Core 7 on my computer...

I blew a capacitor on my old motherboard and bought a new motherboard and installed it blah blah...

so I try to install Ubuntu (my new preference) and as usual I select "start or install Ubuntu" it starts loading...

and after the screen with "Ubuntu" on it along with the loading bar, the loading bar just stops! I try on several other discs including an alternate install CD, it doesn't work... I checked them all for defects and it is all positive and every thing on the discs are fine..

so I try and install Fedora Core 7 (using several CDs), it does the same thing! except this time I get an error thats technically impossible for me to remember at this moment

I cant get linux installed!

what do I do!?

for reference here are my system specs:
**Motherboard:** Asrock P4i65G
**Processor:** Intel Pentium 4 Prescott 2.53GHz
**Video Card:** ATI Visiontek X1550 256mb PCI
**Hard Drives:** 40GB Western Digital SATA and 75GB Maxtor USB


any help would be so greatly appreciated..

---

### Post by Xeeon on 2007-10-30
please someone help me :(

---

### Post by dabl on 2007-10-30
I would first suspect a video issue.  When it is "frozen", after a couple of minutes try Alt-F1 and/or Ctrl-Alt-F1.  If you get a text screen and login prompt, that is the evidence that the installer has failed to autodetect your video card.

You can configure a VESA display (useful until you can install a better driver) by running the ```
sudo dpkg-reconfigure xserver-xorg
``` script.  Just make sure you answer "NO" on the first screen, about autodetecting, and then choose "VESA" on the second screen.  The rest of it should be fairly obvious.  When you finish the script, it will dump you back to the command line.  At that point you can enter ```
startx
``` and you should find yourself at a GUI.

:)

---

### Post by Xeeon on 2007-10-30
I COMPLETELY forgot to mention that, in a few cases after the Ubuntu logo screen with the bouncing bar, it seems to start up normally by telling me "starting preliminary resources....[OK]" and the like, but shortly after that it seems to go through CRAPLOADS of some sort of code (?) and to the left it is counting, for instance "[..153.387492].." and after that is some weird code (it's going WAY to fast to read)

---

### Post by Xeeon on 2007-10-31
all right I've tried and tried everything, it all comes up to this

"[Large integer here] Buffer I/O Error on device fd0, logical block 0"

it displays that error several times and then afterwards many of the same kind of line come up a million miles a second

(Lines like "[Large Integer Here] Random lines of code (?) here")

I am so lost...

on my old motherboard I could install just fine and now... ehh...

---

### Post by Qaazim on 2007-11-11
I too was having my installation hung up on recognizing the x1550 card. Following dabl's advice above was the perfect solution. 

For everything else the script allows you to change, just accept the default or choose the recommend option - you can change things later.

With all the related posts regarding the x1550, we really need to get the word out on this solution.

---

