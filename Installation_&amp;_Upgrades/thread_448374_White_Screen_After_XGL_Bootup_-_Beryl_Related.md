---
title: "White Screen After XGL Bootup - Beryl Related?"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by LASTGUY2GETPS2 on 2007-05-19
If this is the wrong forum please move.

After an upgrade from 6.10 to 7.04 my ati video drivers were lose. I reinstalled them including the addition of a 

    Section "Extensions"
    Option "Composite" "0"
    EndSection 

Section in my xorg.conf. When I try booting into my XGL session with composite enabled my screen is all garbled, when i try logging in with it disabled everything starts off nicely but then I get a white screen (the mouse is visible).  I suspect this is a beryl problem (something about an XComposite plugin missing).

Can anyone please help me? I've done every beryl fix i can find on google. I'm running an ATI x1400 on a IBM T60. xconf in open office file is attached

---

### Post by maino82 on 2007-05-22
I have a similar problem on an Acer laptop with an ATI 1100 IGP. I installed XGL and Beryl 0.2.0 but when I log in the screen is white. If I start a normal Gnome session (without XGL) it works fine. Also, I know it's working somewhat because when I go up to the upper right hand corner of the screen the background turns a different color and there are squares of white windows with full color icons in them that show up (I have Pidgin and Firestarter set to automatically start up when Gnome starts, so those are the icons I see), presumably this is a feature of Beryls, but I don't know for sure since I can't actually use it yet.

Any help would be greatly appreciated.

---

### Post by LASTGUY2GETPS2 on 2007-05-22
I solved the problem (I think) by removing beryl from the synaptic package manager and reinstalled it using a 7.04 guide. Just make sure you have the restricted drivers for your video card working first.

Good luck!

---

### Post by maino82 on 2007-05-30
I've tried uninstalling and reinstalling a few times. My drivers are working fine and X starts up normally with them on. I've tried installing from the ubuntu repo, from the beryl repos, and from a mix where they tell you to install from the ubuntu repo and then take the beryl-xgl from the beryl repo deb. The later is the one that's given me the most success (the white screen) everything else just flat out doesn't do anything. Any suggestions would be greatly appreciated.

Thanks!

---

### Post by LASTGUY2GETPS2 on 2007-05-30
I don't know what to tell you. The order of things I did was 1) Go to synaptic packet manager and uninstall beryl and all associated files 2) Uninstall my graphic card drivers using "Envy" (search for a walkthrough for 2+3). 3) Reinstall my drivers using Envy (you may need to start a nonxgl gnome session 3) Remove beryl sources from my sources.list 4) Reinstalling beryl through synaptic.

To my memory that is what I did. Maybe it was just blind chance. Anyway good luck!

---

