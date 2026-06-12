---
title: "Ubuntu Installation/Upgrade Tips"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by Severun on 2007-12-05
We'll I've been using Ubuntu for almost a year now. I've been through 4 new installs and 5 upgrades, and I must say I'm still impressed. In going through a few installs I found a couple of gotchas that I wanted to pass along in the hopes that it might save someone some time. The Ubuntu community has been very good to me, so as they say, it's time to put back into the pot.

Sound
-------
Under Linux there are older programs that use oss or other methods that take over the sound card so that only one application can play sound at a time. I use artsd, but there is also aoss and other solutions. There's another article [here on this blog]("http://geektravelling.blogspot.com/2007/12/world-of-warcraft-on-ubuntu-gutsy-w.html") that goes into more detail of how to implement artsd, but know that if you only get audio from one program at a time, it's probably because it is using oss or trying to talk directly to the sound card. If you are using wine to run Windows programs you can also run wine under aoss or arts so that it will play nice with other audio apps.

Flash, Windows and Other non-free stuff
-----------------------------------------
The easiest way I've found is to use the Synaptics package manger and install "Automatix". This nifty little program will go out and grab all the non-free stuff you need to play DVD's and other proprietary media on your machine. You can still get the pieces manually by adding the proper repositories and installing the right pieces, but Automatix makes this part a no-brainer.

Video and Network Cards
--------------------------
If you have an ATI or NVIDIA card or certain Network cards you'll probably want to install the non-free drivers for these. Automatix may take care of getting these installed, but if it doesn't, then you'll need to install the restricted drivers package (you can use Synaptics and do a search for restricted). Be sure that you have the "Proprietary drivers for devices (restricted)" checked in Synaptics->Repositories->Ubuntu Software Tab. You want to make sure you check "linux-restricted-modules-xxx" where xxx is the release/architecture of the kernel you are using.

64 Bit Installs
---------------
I did one of these installations and although I was very stoked to be running 64 bit, there was a bit of backbending I had to do to get 32 bit compiled apps to work as not everything is available yet in 64 bit. That being said, most of the important things are available in 64 bit, and you can always compile from source, the things that aren't but if you're lazy like me, 32 bit Ubuntu still kicks **** on anything else on the block.

Games
--------
I managed to get Warcraft, Eve-Online (albiet w/ only oss audio), and Steam w/ Team Fortress 2 working on Gutsy. Games that are written natively for Windoze will always run better there because tools like wine need to create a virtual machine to run the Windoze software. It's nice to be able to say you run games in Linux, but if you want peak performance, you've unfortunately got to run these in Windoze. That being said, if you've got enough horsepower, there's nothing like sticking it to the man in Redmond and running MS Free.

The Nitty Gritty and Support
------------------------------
If you have a problem and have to get into the guts, remember google is your friend, just put Ubuntu as your first keyword and you won't often fail to find an answer. If that doesn't work, posting on the Ubuntu forums has always worked well for me.

Upgrading from earlier releases
--------------------------------
I upgraded and now my video or network doesn't work.  It's probably because you need to re-install the restricted modules for the new release.  Upgrades will disable restricted modules and 3rd party software so after an upgrade be sure to re-install these restricted pieces (I've been bitten by this one more than once).  Also re-installing other applications after an upgrade, or if parts of the install fail, re-installing via apt-get or Synaptics can often set you right.

That's about it for now. Remeber - In a world without fences, who needs Gates?

---

