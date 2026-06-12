---
title: "Current Issues I'm Having With Intrepid"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-10-09
Either myself or someone else reported all of these bugs, and as of right now, none of these are fixed for me. I know that we have time to go before Intrepid goes final, but I'm getting more and more nervous as the release date edges closer. I'm hoping that if any of you are experiencing any of these bugs, maybe you can provide more info in the bug reports to get them resolved. Also, if you guys are experiencing any bugs I've not mentioned, list them. Just like you guys I want Intrepid to be the best release ever and I want to do what I can to help.

Here are my issues:

1.) Gamepads do not work at all. With all of the gamepads I have, pressing any action button crashes X and causes it to restart.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/272421](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/272421)

2.) I have a Gateway M-7315u laptop. I'm having two issues with it in Intrepid, the first is that it takes about two or three minutes to shut down or restart (literally). The second is that the brightness applet and brightness keys do nothing. (So I'm pretty much stuck with a dim screen and can't do anything about it).
[https://bugs.launchpad.net/ubuntu/+bug/280621](https://bugs.launchpad.net/ubuntu/+bug/280621)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/280518](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/280518)

3.) If I install both ubuntu-desktop and kubuntu-desktop on the same machine (so I can switch between KDE and GNOME) both Knetworkmanager and networkmanager start up with Ubuntu. This is a VERY minor bug though, so I'm not too worried about it.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/268803](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/268803)

4.) The line "PCI:XX:YY:Z" is required in the xorg.conf file for my video card to be detected. (I tried it with two cards in SLI and a single card). This was never required before and causes a large number of people with certain nvidia cards to not even be able to reach bulletproof X, let alone a usable GUI.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/263768](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/263768)

5.) Zsnes will not run in Ubuntu. I tried it in a 32-bit install as well as 64-bit. With Hardy and prior, it ran just fine in 32-bit and 64-bit. Of course in 64-bit you have to force the architecture, but that's always worked fine. There was a fixed package in the bug report that causes Zsnes to run fine in 32-bit, but it does not fix it in 64-bit.
[https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425](https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425)

6.) Some Lexmark printers are completely broken. Basically the Z600 or anything that uses the same driver as the Z600. It worked fine for me in Hardy and prior, but no longer.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/276162](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/276162)

As you can see, some of those bugs are really horrible, and some of them are very minor. With the final release of Intrepid being in just a few weeks, I'm nervous to see such horrible bugs this close to release. I do understand it's a beta, and I do understand that there's still time to fix them, yet the more time that passes the more nervous I get.

---

### Post by kforum on 2008-10-10
hey there,d o you volume up/down keys work?
on mine the brightness keys are buggy too, but the volume ones are even more inexpressive.
also, i use nvidia too, and yeah everything is kind of sluggish atm, but it is beta, so im not minding that particular fact way too much.(it seems everyone is having some graphical issue)

on the restart though, my hint is update-and-restart, then update again and restart, it seems the more i restart the smoother it gets. :P just kidding, but anyways, always keep updating, it will fix some minor nuisances. my splash was broken and fixed its self, even though it sometimes chooses not to work(lazy bumps). and my restart also shows strange graphic behavior sometimes, but not most of them.

cheers.

---

### Post by jlacroix on 2008-10-10
> **kforum said:**
> hey there,d o you volume up/down keys work?
on mine the brightness keys are buggy too, but the volume ones are even more inexpressive.
also, i use nvidia too, and yeah everything is kind of sluggish atm, but it is beta, so im not minding that particular fact way too much.(it seems everyone is having some graphical issue)

on the restart though, my hint is update-and-restart, then update again and restart, it seems the more i restart the smoother it gets. :P just kidding, but anyways, always keep updating, it will fix some minor nuisances. my splash was broken and fixed its self, even though it sometimes chooses not to work(lazy bumps). and my restart also shows strange graphic behavior sometimes, but not most of them.

cheers.

On my Gateway laptop all the buttons work fine except for the brightness keys. Even the volume keys work, but it's difficult. It's difficult in Vista too, so it's not Ubuntu's fault, it's the hardware. Using the volume icon is no big deal to me though.

---

### Post by bubba_169 on 2008-10-12
Same problems here with the brightness - everything else including volume works perfect. All worked well in Hardy.  I think it worked well in windows too but cant remember, this c640 hasnt seen windows since before vista was released.

---

### Post by jlacroix on 2008-10-12
I'm still having the gamepad issue, I really hope it's fixed before release. :(

---

