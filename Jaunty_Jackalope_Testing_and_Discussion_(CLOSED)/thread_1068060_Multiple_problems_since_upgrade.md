---
title: "Multiple problems since upgrade"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rednick on 2009-02-12
I decided to give the new alpha 4 a look, since I use my machine essentially for web and multimedia work.  The "Aperture >4GB" problem in Intrepid breaks VLC - my preferred media player and so, whilst I knew there may be issues, I decided to have an early peek at Jaunty.

Oops.

Firstly, when booting either from Jaunty hard drive install (done with update-manager -d from intrepid) or from the subsequently-downloaded live CD, I get this at startup - sorry for the big image but we'll come to that later:
[IMG]http://img4.imageshack.us/img4/9163/dsc00455vb1.jpg[/IMG]

Boot continues normally and I can log in.  My desktop opens but with the wrong icon set and colours for things like taskbars, window decorations etc.

Most software doesn't work.  Anything using gStreamer is a non-starter - Totem will not open, Pidgin opens and immediately crashes, no photo viewers or editors work and Firefox closes itself down if I navigate to any site using flash.  This is independent of whether I use Gnash, flashplugin-nonfree or the X64 alpha of adobe-flashplugin (which incidentally was lightening quick under Intrepid).  No flash at all is the only way.

When I launch the system monitor I find that there are around 50 instances of gnome-power-manager running, over a hundred of gnome-settings-daemon and five or so of Pidgin.

Other broken apps include Thunderbird (don't like Evo so haven't tried it), Open Office (crashes X) and of course Compiz.

On the plus side VLC works :lolflag: and so does VirtualBox.  So I now have 8.10 installed in a virtual machine to run everything else!  Apart from this meaning about a 3-minute total boot time I can live for now.  However, any thoughts on the myriad of problems I'm suffering would be much appreciated.

FWIW, system is as follows
ASUS K8N4-E mainboard, Athlon S754 3400+, 1.5GB RAM, ATI X850XT-plat-ed using opensource driver.  LG GSA-H42N DVD-multi drive, 1x WD 40GB IDE HDD, 1x WD 250GB IDE drive (primary master and slave respectively) and a Samsung 500GB SATA drive.

Anyone else having similar issues?

---

### Post by Kevbert on 2009-02-14
Looks like you have some hard disk problems. Once you've booted have a look at the following command in terminal:
```
man badblocks
```

---

