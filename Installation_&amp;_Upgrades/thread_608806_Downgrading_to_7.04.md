---
title: "Downgrading to 7.04"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by jleino on 2007-11-10
Hello.

Has anyone else had major problems with 7.10 release? Personally I'm considering seriously downgrading back to 7.04 which worked pretty well with me. I have and old IBM T30 laptop.

- xorg configuration fails. I have external wide screed display and the graphics adapter is not able to drive it simultaneously with the laptop's original display. That is why by default the external display geometry is incorrect. The previous release shut down the laptop's own display when I closed the lid and the external monitor was ok. Does not work any more. The display switch buttons don't work. It took me a while to figure out that xrandr --output LVDS --off makes the trick. Now I need to issue this command every time I log in. The graphical resolution and display geometry applets are pretty much useless - I don't know if they doanything. At least nothing changes when I press the buttons.

- No sound. In previous version that worked. I can't remember if I had to manually tweak something though.

- USB memories (mass storage devices) don't work any more

- The last straw was now that the document viewer stopped working and everything else seems to be pretty sluggish also.

jleino@mnemonic:/media/cdrom/Doc$ evince

** (evince:6948): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I tried upgrading first, but later did a fresh install after problems with the display. Fresh install didn't help.

I'm not really interested with compiz/eyecandy stuff at all. Is there a way to make an install without them completely?

Please help. I need my computer!

With best regards, Juha, a long time Ubuntu user.

---

### Post by Nano Geek on 2007-11-10
You can install Ubuntu Server Edition and then select only the packages you want.

---

### Post by handzmonkey on 2007-11-10
I had issues with 7.10.  I upgraded from 7.04 Ubuntu Studio and performed a clean install.  The first big issue I had with 7.10 was that it felt bloated.  It took forever to boot up, and my laptop isn't slow.  Then I had the compiz issues that in short drove me to downgrade back to studio.  I have decided to wait for the next release as it will be a LTS.  The biggest down side to running 7.04 is that there are no more updates.

---

### Post by foxmulder881 on 2007-11-10
To the OP, have you tried a clean install?
I had all the same probs as you when I upgraded from 7.04, but then I performed a clean install of 7.10 and everything was fine.

---

