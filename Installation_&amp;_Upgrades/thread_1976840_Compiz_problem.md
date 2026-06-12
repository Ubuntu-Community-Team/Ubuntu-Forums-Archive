---
title: "Compiz problem"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2012-05-09
Totally bad initial experience.  Planned to do a clean install on a test system running 10.04.  Booted amd64 CDROM and display is synced but unreadable streaky blocks in the windows & buttons -- cant read anything :(

Blindly clicked where the "Try" button should be, and eventually a desktop came up but it froze after some cutesy "effects" started when I moused over a distortedly drawn icon on the desktop.

I've been using LTS releases since 6.06 and each has initially had more problems than the one before it for me.


Edit:
Hitting tab during startup to get the menu, the CDROM passed the "integrity check".  Seems there is no text mode install option, I'll see if nomodeset helps before I download Mint :(

---

### Post by zeljkojagust on 2012-05-09
You sure you don't have a GPU problem?

---

### Post by Mopar1973Man on 2012-05-09
Video driver issues? 

Kind of the reason I'm holding back a little bit is to give the rest of the world a shot at catching up to Ubuntu 12.04 with drivers and such. I would sure hate to upgrade and find out the drivers for my nVidia card are not going to work properly or maybe my printer.

I'll eventually job on the upgrade but for the time being I'm holding back for a bit... ;)

---

### Post by zeljkojagust on 2012-05-09
Not the drivers, but the graphics card itself. Do you have another one you can replace with your current one?

---

### Post by kelvin spratt on 2012-05-09
> **wkulecz said:**
> Totally bad initial experience.  Planned to do a clean install on a test system running 10.04.  Booted amd64 CDROM and display is synced but unreadable streaky blocks in the windows & buttons -- cant read anything :(

Blindly clicked where the "Try" button should be, and eventually a desktop came up but it froze after some cutesy "effects" started when I moused over a distortedly drawn icon on the desktop.

I've been using LTS releases since 6.06 and each has initially had more problems than the one before it for me.


Edit:
Hitting tab during startup to get the menu, the CDROM passed the "integrity check".  Seems there is no text mode install option, I'll see if nomodeset helps before I download Mint :(
use the alternative install disk there is a problem for some with the live CD.

---

### Post by wkulecz on 2012-05-09
The nomodeset boot option got me dialog boxes I could read.  I checked "download updates while installing" and "install third party software" and alls well that ends well.

It automatically installed the binary Nvidia driver (current version), my question is what is there to know about the (current version-updates) driver offered when I went to install the binary driver?

YouTube works out of the box, very nice!  Now to install all my development tools and libraries.

I don't like Unity so I may install something else, but Unity should be fine for the folks who use these "appliance" computers (who don't know or care that its Linux underneath) assuming I can add my programs to the dock.


Edit:
Perhaps the "nomodeset" option should be a bit more prominent and labeled as something to suggest trying it if the initial boot up display is not usable.

---

### Post by wkulecz on 2012-05-09
Spoke too soon, compiz crashed while using the Dash to try and find synaptic.  I don't need any cutesy crap "effects" so I'll see if I can figure how to just keep it always off.

---

### Post by mörgæs on 2012-05-09
Please use a more informative thread title.

---

### Post by kurt18947 on 2012-05-09
> **wkulecz said:**
> Spoke too soon, compiz crashed while using the Dash to try and find synaptic.  I don't need any cutesy crap "effects" so I'll see if I can figure how to just keep it always off.

You could always use 'gnome classic', xfce-desktop or something along those lines.  I've had good luck installing cinnamon from the ppa but others have reported problems.  If you do try cinnamon, do not include muffin.

---

### Post by wkulecz on 2012-05-09
Seems one of the 103 updates (installed with apt-get update ; apt-get upgrade seems to have fixed it, hasn't crashed since, but I'm mostly just been using synaptic to install the libraries and tools I need.

---

