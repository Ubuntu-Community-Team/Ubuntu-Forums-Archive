---
title: "Upgrade or reinstall?"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by sailor420 on 2005-10-23
I'm currently running Hoary and looking to upgrade to Breezy. My question is, would it be easier/better to upgrade, or just reinstall? Is there a seriously good chance of borking everything if I upgrade?

Thanks!

---

### Post by Kyral on 2005-10-23
Eh its 50/50. It depends on how easy a clean reinstall would be for you. If you know how to fix stuff when it breaks (Like it might on a dist-upgrade) then go for the upgrade. If you dont and a clean reinstall would be easy for you then go for the reinstall

---

### Post by Psquared on 2005-10-23
[QUOTE=sailor420]I'm currently running Hoary and looking to upgrade to Breezy. My question is, would it be easier/better to upgrade, or just reinstall? Is there a seriously good chance of borking everything if I upgrade?

Thanks![/QUOTE]

I would say the chances of borking everything are slim < 10%. The chances of borking something are pretty good. > 50%. I managed to do the upgrade and the only problems I had were with old Firefox extensions and wireless. I did manage to fix most everything by hacking around and reading here.

Frankly I prefer the upgrade route because I don't have to worry about reinstalling stuff. (I would make a backup of your personal stuff just in case.)

Now that I've got Breezy stabilized I like it a lot. Much better than Hoary, which was a definite improvement over Warty. Warty to Hoary was a bigger jump in terms of visible changes. Hoary to Breezy is much less obvious. Its mostly under the hood stuff.

---

### Post by pauljwells on 2005-10-23
I just did an upgrade on both my mac and pc ubuntus. The mac one went smoothly, the pc one threw up a couple of problems:

The main one was the 3D graphics on the ATI card, Xorg didn't load so I got a console at login. No problem, I kept a copy of my first xorg.conf with vesa drivers and no dual head support - very basic but got me a gui. After that I found I had to use synaptic to install gnome-desktop, since some of the new gnome features didn't automatically get installed. I uninstalled the old ATI fglrx driver using the uninstall shell script and then installed the updated one from synaptic (the hoary fglrx official package didn't work, you had to use the ATI installer, which was a mess, frankly), reloaded my bells ' n ' whisles xorg.conf and everything worked perfectly. I'd spent quite a while sorting out samba and sound on hoary that I didn't want to risk getting it wrong on a reinstall. I'd recommend the upgrade route, if you have problems just ask...

Good luck. It's worth the upgrade whichever way you do it. Ubuntu was already good, now it's great!!

---

### Post by brentoboy on 2005-10-23
dual boot

if all goes well, reclaim the old space.
If it has issues, you can always go back.

---

### Post by sailor420 on 2005-10-24
Just finished with the dist-upgrade. I got a couple of issues which the guys in the IRC channel helped me fix, but everything *looks* to be working fine now. Thanks!

---

