---
title: "Dosbox problem"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by elfuego on 2007-05-22
Hi all :)
I removed Mandriva, put on Ubuntu - and just as when I thought that everything works flawlessly - this happends. I instaled dosbox 0.70 with a little trouble because I had to download and install some packages to get GT/glu.h - but in the end everything went fine. Now, when I try to start dosbox I get this message:
"Exit to error: Can't init SDL No available video device"

I installed literally every single package that had any "SDL" in it with the Synaptic package manager - and it still doesn't work. Any ideas?

10x!

---

### Post by elfuego on 2007-05-23
Hi, I found in google that somebody else had the same problem and solved it, but I don't understand polish :) Can anyone help me? It's here:
[http://forum.ubuntu.pl/viewtopic.php?=&p=146249](http://forum.ubuntu.pl/viewtopic.php?=&p=146249)
10x!

---

### Post by kwalo on 2007-05-23
Everything, that needs to be done is to type:
```
sudo apt-get install libsdl1.2debian libsdl1.2debian-alsa libsdl-net1.2 libsdl-sound1.2
sudo apt-get install dosbox
```

---

### Post by veerakumar on 2007-05-23
You need to run in X11 desktop
dosbos needs libsdl
and libsdl needs any supported video device
like x11 svgalib etc

---

### Post by elfuego on 2007-05-24
> **veerakumar said:**
> You need to run in X11 desktop
dosbos needs libsdl
and libsdl needs any supported video device
like x11 svgalib etc
Hmm... I am running GNOME with beryl, AIGLX on ATI Radeon Mobility 9600 with ubuntu open source drivers. Can this be a problem? I have svgalib and I tried editing libvga.config but it didn't help.

@kwalo
Thanks, I tried that - but it did nothing: 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2debian is already the newest version.
libsdl1.2debian-alsa is already the newest version.
libsdl-net1.2 is already the newest version.
libsdl-sound1.2 is already the newest version.
The following packages were automatically installed and are no longer required:
  mplayer-skins liblame0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
dosbox is already the newest version.
The following packages were automatically installed and are no longer required:
  mplayer-skins liblame0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by elfuego on 2007-05-24
Well... It didn't work out with native linux dosbox, but I did get the things done (the hard way) with wmvare tools, win98 and dosbox 0.63 in it (0.70 didn't work in 98). Works like a charm now ;)

I am still interested in a linux solution to this problem though...

---

### Post by elfuego on 2007-05-25
I did manage to install dosbox, but only version 0.65-1, and I did this: First I searched for every instance of "dosbox" in "filesystem" and deleted it. I removed every single trace of it I had found. Then I typed this in console:
```
 apt-get install dosbox --reinstall 
```
and it worked afterward. But that wasn't what I wanted - as I wanted the new version, 0.70, so I unistalled it from synaptic package manager and tried a new, clean, instalation of dosbox 0.70 according to this guide:
[http://gaming.gwos.org/e107_plugins/content/content.php?content.39](http://gaming.gwos.org/e107_plugins/content/content.php?content.39)
And, again, I get this as a result:
```
Exit to error: Can't init SDL No available video device
```
Then, I repeated the steps that I made and installed 0.65-1 version, again. Now I have dosbox, but it's not 0.70. Funny thing is that 0.70 doesn't work in Windows98 either. Is there something wrong with that version? :roll:

Anyway - thank you all for your help!

---

