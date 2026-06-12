---
title: "Ubuntu + 680i + 8800 GTX = no love"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by flimflam on 2007-03-12
So to begin with I run Vista, XP, Mandriva, and Ubuntu.  I recently tried Mandriva but actually love Ubuntu.  Since I got an 8800 and switched to a Macbook, I have not been able to run Ubuntu though.  

So my setup is:

e6600
Auss p5n32-e mobo (680i chipset)
8800 GTX

I have worked out the issues with the 8800 + 680i in mandriva but not in Edgy.  I am not a complete noob, but am still a beginner at Linux.

Anyway, I have to use the alternate cd install since the 8800 causes problems.  I mounted a cd with the new Nvidia drivers, but when I tried to install them, I get:

"please install your distribution's libc development package"

So I tried:

```
sudo /etc/init.d/gdm stop

```

Also, Ubuntu has problems with the 680i chipset, and none of my ethernet ports work, so I cannot get updates via internet. I tried adding

```
options forcedeth msi=0 msix=0
```

to etc/modprobe.d

but that did not solve he ethernet problem.

So basically I cannot start the x server, and am having problems installing the nvidia drivers, and have no ethernet. 

Any suggestions?

[COLOR="DarkRed"]EDIT:

I did:

```
sudo apt-get install build-essential
``` which installed the needed libraries and I was able to install the nvidia drivers, so I am golden there.  However, I have no sound and ethernet.  I can probably figure out the sound and compile ALSA drivers for it since I think Asus might have drivrs for this.  However, ethernet is important, obviously.  Any ideas?  The forcedeth does not work....[/COLOR]

---

### Post by cprofitt on 2007-04-14
Hmm...

This is one of the chipsets I was considering... I guess it will not fly.

---

