---
title: "HP Pavillion ZE4600 laptop"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by coopcoop on 2013-01-17
Have done successful installs before but now am trying to install Ubuntu on an HP Pavillion ZE4600 laptop that previously had Win XP on it. The installation was failing, so I thought the hard disk was bad. Bought a new one - 80 Gig - but same problem. The installation will not format the drive. Should I format it first on a Mac or PC? I assumed the Ubuntu installer would format it as needed. Thanks!

---

### Post by mörgæs on 2013-01-18
Welcome to the fora.

This one is too old for Ubuntu, but you could give Lubuntu a try. 

How much memory does it have?

---

### Post by SonnyE on 2013-01-18
I'm running an HP Pavilion ze4800 (aka ze4805us) on Lubuntu 12.04 right now. The biggest hurdle in setting it up was after booting from the live CD and trying to install to a partition, the installer would freeze up halfway through instead of finishing. I solved it by uninstalling the "Ubiquity slideshow." These old laptops can't handle the advanced slideshow during installation.

Here's a command to use for that:

sudo apt-get remove ubiquity-slideshow-ubuntu

according to this page:

[http://askubuntu.com/questions/139698/ubuntu-12-04-lts-installer-crashes](http://askubuntu.com/questions/139698/ubuntu-12-04-lts-installer-crashes)

I don't know if the slideshow is a problem in 12.10, and I don't know if you've already got past the slideshow problem and are running into some other problem, but if you haven't got past the slideshow problem yet, this is info you need.

---

### Post by Nr90 on 2013-01-18
I suppose you could also use the alternate installer.

That said I think ubuntu dropped support for non-PAE processors after 12.04, which I assume includes yours.

---

### Post by coopcoop on 2013-01-21
Thanks - will give that a try!

---

