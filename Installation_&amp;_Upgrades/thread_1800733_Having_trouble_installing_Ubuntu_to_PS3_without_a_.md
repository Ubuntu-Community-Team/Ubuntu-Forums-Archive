---
title: "Having trouble installing Ubuntu to PS3 without a CD"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Cuthlif on 2011-07-09
So I happen to have an old PS3 that still has the option to install other os (Bought a new one when the laser on the old one crapped out)

So I'm trying to install Ubuntu on it via USB so I can use it as a web browser on my new TV.

I've already formatted the internal HDD (60g) and set up kboot, but I'm having a lot of trouble trying to get it to actually install.

I've got the image of 9.04 for PPC+PS3.

I've tried both unetbootin-win-549 and Universal-USB-Installer-1.8.5.7 to install the image with, but each time I boot up into OtherOS and then into kboot, I keep getting a message about 'root fs not found blah blah blah'

Help?

---

### Post by earthmeLon on 2011-07-09
Hey!  Glad to hear your interest in using Linux on your PS3, but sad you're having such difficulties.

[http://wiki.gitbrew.org](http://wiki.gitbrew.org) has a *LOT* of information about installing many different distributions of Linux on different versions of PS3.

You said you were using OtherOS (original, vs OtherOS++)?  Does this mean you're on 3.15?

Maybe these instructions will help you get your PS3 up and running:  [http://www.elliptique.net/wiki/doku.php?id=fedora12-ps3](http://www.elliptique.net/wiki/doku.php?id=fedora12-ps3)

If that doesn't help, I am sure you will be able to figure everything out using Gitbrew's wiki, as well as asking questions on their IRC server.


I've seen a few issues with installing/running Ubuntu, although it is very possible and not too hard to get working.  Debian seems to be the cleanest to install.

Most people use a chroot method of installation from OtherOS/petitboot to get Linux working.  You can try using a debbootstrap of Debian/Ubuntu.

If you are unsure what any of this means, just wait for [Gitbrew]("https://twitter.com/#!/gitbrew") to get their stuff together.

---

### Post by Cuthlif on 2011-07-09
Thanks for those. I'm having some trouble opening up that link to gitbrew site, and unfortunately the other link you posted isn't applicable to my situation as the disc drive on my PS3 is shot.

I have however stumbled upon a potential (convoluted) solution involving wubi and a virtualization of a PPC 'nix image.

I'll post my results when I have them.

---

