---
title: "System Requirements"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by Dirk Bock on 2005-11-09
Hi folks,

due to one of our PCs buying the farm, I try to resurrect an old one as temporary measure. Now I'm tempted to set up Ubuntu on this machine, but will it work on a 8 MB 486DX2-66?

I know this sounds like a troll, but back in the old days I remember running a Linux version on a 486-33 machine. So maybe...:rolleyes: 

Greetings

---Dirk Bock

---

### Post by Kyral on 2005-11-09
Ubuntu has been known to run on pretty old hardware, but this one may be pushing it. I mean I'm sure you could get a very minimal install going, but don't expect to be able to run X

---

### Post by phanboy_iv on 2005-11-09
You might (dare I say it?) want to try another distro if Ubuntu doesn't suit your 
old machine. There are a few designed exclusively for older hardware, but of course
a command line is all you're gonna get with a 486.

---

### Post by az on 2005-11-09
Good question.

You need a lot more ram to install and run Ubuntu.  You need 16 megs of ram to install Debian Woody!  After then install, though, you can run Woody with 8 megs of ram (maybe four?)

Ubuntu requires 64 megs of ram to install.

---

### Post by Kyral on 2005-11-09
Damn Small Linux anyone?

(WTF is this? This is the second time I've reccommended someone use DSL on these Forums in the past week! :P)

---

### Post by Dirk Bock on 2005-11-09
Hmmh, I thought that much. :(  Guess my X-ambitions have to wait 'till we invest in a new PC.

Thanks for your quick ansers!

Greetings

---Dirk Bock

---

### Post by Zitchas on 2005-12-05
Although I'm not faced with such a situation myself at the moment, I must find it odd that I can't find any sort of system requirements, or even guidelines, anywhere.

From what I can gather it'll run on *almost* any system, but are there any generally agreed on minimums for running the latest versions decently?

Thanks

Zitchas

---

### Post by SickTwist on 2005-12-06
[QUOTE=Zitchas]Although I'm not faced with such a situation myself at the moment, I must find it odd that I can't find any sort of system requirements, or even guidelines, anywhere.

From what I can gather it'll run on *almost* any system, but are there any generally agreed on minimums for running the latest versions decently?

Thanks

Zitchas[/QUOTE]

The thing is that "running decently" is quite relative. Obviously Ubuntu will run faster with newer hardware and slower with older hardware but there is a lot of gray area which is probably why you have not seen any specific system requirements nailed down. One thing is fairly certain though: less than 64 MB of RAM and Ubuntu will be difficult (if not impossible) to install. The default install takes about 2 GB of space but there are ways around that if you have a smaller HDD.

I would suggest that if you want to use X and run in graphical mode then do not expect to do it on less than 96 MB. Even then though, you will have to use a minimal window manager like [Fluxbox]("http://fluxbox.sourceforge.net/").

I have a Pentium MMX 233 Mhz with which I have been experimenting. It had 112 MB of RAM but I upgraded it recently to 192 MB. It is running Breezy with GNOME. I did some tricks in GNOME to gain performance (disabled icons on desktop, disabled window manager animations, disabled background image, used one panel with very few applets, etc) and it does run, but slowly. I realize that I could use another desktop but I wanted to see how far I could push GNOME.

Hopefully that gives you some idea of what to expect. If you are trying to install Ubuntu on a Pentium II or Pentium III-era machine then you will have better results. If you use a lighter desktop than GNOME (Fluxbox, Blackbox, IceWM, XFCE) then you will have even better results. If you want to run GNOME you'll need about 128 MB of RAM or Ubuntu will swap like crazy.

There are some memory hungry programs that should be avoided (Firefox, Thunderbird and OpenOffice for example) and there are some lighter programs that you may wish you try like AbiWord (word processor), Gnumeric (spreadsheet), Leafpad (text editor), Dillo (minimal Internet browser), Epiphany (another Internet Browser), and Sylpheed (e-mail client) to name a few.

Good luck with it!

---

