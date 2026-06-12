---
title: "X Server fails to start after install or for liveCD w/ Ati Graphics *SOLUTION*"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by JayEmm on 2007-09-05
OK Guys, this is a big problem, thought I'd post my solution for y'all to see...

Anyway, this assumes you've popped in a livecd, run a text install to get the blue screen with the Xserver error and then got dumped into a BASH shell (Command Line)

Your best bet is to download ENVY, an automatic graphics driver script.

Type:

wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

then

sudo gebi envy_0.9.7-0ubuntu8_all.deb

then

when that's done

envy -t

And choose the appropriate option (normally 3 then enter for Ati cards)
This does require a working network connection, 
This will download and install the driver, reply Y to the Xorg config (unless you have good reason not to) but if you are running a LiveCD, do NOT restart!

Then, choose option 7 to restart the Xserver and... should work!

I hope the Ubuntu guys fix this for the Gibbon, it's a major problem and not the easiest to work around!

Peace.
JM.

---

### Post by southernman on 2007-09-05
Sounds like a nice work-a-round you found but...

FYI - this isn't a problem with Ubuntu. The problem AFAIK, rest solely on the lack of support from ATI itself.

You may say... but brand X GNU/Linux distro supports this or that ATI card. Well, that's true some do. Ubuntu on the other hand tries to keep itself separate from using proprietary stuff that isn't legal to use in all areas of the globe. Multimedia support is a prime example of Ubuntu's philosophy again. Sure, you can download the libs to play all media, but your warned that doing so may be illegal and lays the burden to find out / know if they are legally able to use the stuff.

Back to the topic of ATI support (or lack thereof for linux). A lot of ATI cards are supported in Ubuntu, but those that are have drivers that have been hacked/modified to work. I personally have 3 ATI cards in use, and don't need a restricted driver for any of them... they all just work. When I do upgrade my hardware again... bet your sweet **** there won't be an ATI card coming to my door! Vote with your dollars too.

Again, nice fix. I'll bookmark it and refer others that may be able to use it.

PS. Would it work in your how to if instead of referring to a specific version of envy, you just refer to envy itself?

---

### Post by Sugyi on 2007-09-05
THX for this solution, seems no too hard and my first to find. The strange thing on the whole is that, Ubuntu 6.06 easily starts, it is a problem of newer versions, wondering why.

Although for me this solution does not help, because I do not even come to a command line, I just do not get anything written on the lines, just empty lines. It is possible for me to write, but my machine simply does not respond. Any advice?

---

### Post by JayEmm on 2007-09-07
How far does the install let you go, are you using a LiveCD or alternate install? If you really want ubuntu, maybe try the alternate disk. It's fiddlier but still easy to use...

---

### Post by Sugyi on 2007-09-07
My system is already installed. For me the LiveCD did not work, nor the save graphics mode so I tried the alternate CD you mentioned, I have installed and when booting this happened to me. I have no username%something on the beginning of the lines. Although, my system seems to respond, because when I push the power button it starts to kill the processes and switches off.

---

### Post by Sugyi on 2007-09-10
Now I reinstalled with Ubuntu 6.06LTS. I'm thinking about an upgrade to 7.04 and then maybe to the new 7.10 Tribe 5, but I'm worrying about the same problem to appear after the upgrade, is it possible to avoid it?

6 October 2007
Finally got some time to play, so I upgraded step by step until Gutsy Beta, so my method work if anybody is interested.

---

