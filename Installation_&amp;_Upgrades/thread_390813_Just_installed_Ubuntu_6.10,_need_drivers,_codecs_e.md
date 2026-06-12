---
title: "Just installed Ubuntu 6.10, need drivers, codecs etc."
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by ROUBOS on 2007-03-22
Hi all,
I just installed Ubuntu 6.10 on my spare system and at the moment I'm downloading the ATI drivers from the ATI site.

What I would like to ask is if people could direct me in getting players codecs for DVDs, music, videos etc.

I'm also gonna try and get an OSX look. :)

Specs:
Gigabyte KT600 mobo
AMD AthlonXP 2400+
1Gb RAM
ATI Radeon 8500 128mb (old I know waiting for a new one)
SB Audigy

OK just downloaded the drivers from the ATI site. 
I right clicked on the file. Clicked on the option to allow run as executable. I double-clicked on it and ran it in a Terminal window.
So that did it?

And how do I get my monitor resolution to 1440x900
It's not listed :(

---

### Post by Kateikyoushi on 2007-03-22
Read this about installing codecs. [LINK]("https://help.ubuntu.com/community/RestrictedFormats")
To get themes go to gnome-look.org.

Stick with installing from the repositories it is safer and easier. This mught be a good thing to read.

To configure X run this in the terminal.
> sudo dpkg-reconfigure xserver-xorg

---

### Post by wpshooter on 2007-03-22
> **Kateikyoushi said:**
> 
**Stick with installing from the repositories it is safer and easier. **

BOY, I really do agree with this !!!

---

### Post by mcduck on 2007-03-22
For fglrx drivers, you should run 'sudo aticonfig --initial' to create correct configuration for X.

---

### Post by ROUBOS on 2007-03-22
So what do I do to get the ATI drivers for my card from the repository? (Radeon 8500)

---

### Post by wpshooter on 2007-03-22
> **ROUBOS said:**
> So what do I do to get the ATI drivers for my card from the repository? (Radeon 8500)

Go into Synaptic and search for by NAME, "fglrx".  I think there are 3 files that you need to check and install.  That is step one.

Then you need to edit the video card section of your /etc/X11/xorg.conf file and replace the ATI driver parameter with fglrx.

Good luck.

---

### Post by mcduck on 2007-03-23
> **ROUBOS said:**
> So what do I do to get the ATI drivers for my card from the repository? (Radeon 8500)

In short:

1. 'sudo apt-get install xorg-driver-fglrx'
2. 'sudo aticonfig --initial'

You might also need to add following code to the end of your xorg.conf:

```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

---

### Post by sedition on 2007-03-23
Another good source of info when setting up a new Ubuntu installation (codecs, flash, media players, etc.) is this [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

---

