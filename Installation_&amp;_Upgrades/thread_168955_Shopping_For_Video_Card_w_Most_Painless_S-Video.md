---
title: "Shopping For Video Card w/ Most Painless S-Video?"
date: 2006-05-01
forum: Installation &amp; Upgrades
---

### Post by abbot on 2006-05-01
I came across an old dell for cheap.  I wan't to hook it up to the TV to get some movie action goin.  I don't need any DVR recording capabilites.  Just use the TV as a monitor.  I wan't to get a card that will make that as painless as possible.  I'm not afraid to edit text files & such, but i'd still prefer not to if I don't have to.  I believe this box has a PCI video card slot.  There is an old voodoo 3dfx card in there right now which does have a s-video output, but i've researched and read that there isn't any way to get it working with linux.

---

### Post by hollywoodb on 2006-05-01
I recommend nvidia, any old card with a TV-Out/S-video.... 

In a terminal, ```
 less /usr/share/doc/nvidia-glx/README.txt.gz 
``` will give you the documentation for the driver you have installed (once you install the nvidia-glx package).

If you don't have nvidia-glx installed (which you probably don't being your system has a voodoo card), [this page]("http://www.nvidia.com/object/unix.html") will take you to the newest nvidia drivers.  From this page you can click on the driver you'll be using (IA32 for for your system) and view the README.  In the table of contents you can find the section that lists supported nvidia cards and X config options to enable TV-Out.  Ubuntu Breezy uses driver version 1.0-7667.  You can view the README for that driver if you click the 'archive' link below the IA32 driver on the first link I posted.  Your best bet is to pick a nvidia card that is supported in the 1.0-7667 and latest driver versions.  Sometimes really dated cards are left out to dry, and its nice to know that nvidia is still supporting yours.

I **highly** recommend you use the nvidia drivers that are available for Ubuntu from the repositories, **NOT** the prepackaged nvidia drivers available at those links.

---

