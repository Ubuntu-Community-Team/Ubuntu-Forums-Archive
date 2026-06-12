---
title: "Ubuntu Load Error"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by cyriax on 2011-02-17
I have dual booted ubuntu 10.10 32bit with windows 7 64bit. Once grub comes up if I choose w7 it will load straight away, if I choose ubuntu a flashing hyphen will appear in the top left corner and just sit there. I have left it for over an hour and it is still at the same loading point.

My hardware is:
GFX: 2xGTS 450's
CPU: Phenom II x6 2.8GHz
MB:  ASRock 890FX
RAM: 2x4GB G.SKILL
PSU: 900w Antec

I have tried both 10.10 and 10.04, I am going to try Fedora 14 to see if it is consistent with w7 and then erase my hard drive and just single boot ubuntu.

---

### Post by Sean Moran on 2011-02-17
> **cyriax said:**
> I have dual booted ubuntu 10.10 32bit with windows 7 64bit. Once grub comes up if I choose w7 it will load straight away, if I choose ubuntu a flashing hyphen will appear in the top left corner and just sit there. I have left it for over an hour and it is still at the same loading point.

My hardware is:
GFX: 2xGTS 450's
CPU: Phenom II x6 2.8GHz
MB:  ASRock 890FX
RAM: 2x4GB G.SKILL
PSU: 900w Antec

I have tried both 10.10 and 10.04, I am going to try Fedora 14 to see if it is consistent with w7 and then erase my hard drive and just single boot ubuntu.
I often get that flashing hyphen, (usually @_), when I'm testing out new distros, and generally find that I've removed something critical from the files or packages in the .iso I'm testing.

No solutions on such a broad problem, except that pressing CTRL+ALT+F1 might take you to the console screen that might have left an error message related to why the screen you'd expect to bring up the splash image is stuck with that hyphen.  I hope that might show the way to find out what the last error was.  Sometimes there are more than one page full of errors, but it's easier to start with the last one and work backwards until you get to the login screen.

PS: A long time ago, one of the causes for this same failure was due to my installing the 'restricted drivers' for my nVidia 185 video adaptor before the installation.  I soon found that just installing everything offline and avoiding any 'restricted drivers' whilst on the Live-CD until the basic system was happily married to the hard disk partition overcame the problem, although how this happened, I never bothered to test out any further once I'd learned to NOT install anything extra to the Live-CD until AFTER the HDD installation was done..

---

