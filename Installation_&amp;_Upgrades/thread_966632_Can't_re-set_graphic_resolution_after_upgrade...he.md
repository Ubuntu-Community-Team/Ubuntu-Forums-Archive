---
title: "Can't re-set graphic resolution after upgrade...help!"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by GIMEL on 2008-11-01
Hi Folks,
I upgraded from the Harty Heron to the Intrepid Ibez. All was well until I ran into the graphics resolution quary. I gave me only two very low choices. I selected the one other than the one it was set to and it became scrambled. I can log in but I cant see the screen well enough to select anything.
I have tried to dpkg-reconfigure and get no change.
I have tried to edit xorg.conf, but was not succesful. 
I saw a post were someone mentioned adding the resolution manualy in the xorg.conf.
I couldnt find that post again. Does anyone know how to do that?
I have a sony viao with Ubuntu as the only OS.
The system worked great for months with Hardy.

---

### Post by noctiphile on 2008-11-01
I had the same thing happen with my NVidia card.  X.Org doesn't support the proprietary driver in 8.10.  There was a note at the beginning of the upgrade that said that.

Try using displayconfig-gtk to change your monitor and graphics card to the correct settings.  It's also under the System -> Administration menu, called "Display Settings & Hardware," or something close to that.  It worked for me when this happened when I upgraded to 8.04.  That program disappeared on me when I upgraded to 8.10 though.  Hopefully you still have it.  I could not find it with Synaptic to reinstall.

Also there is a way to change the Panel size as a boot option to the kernel.  You just add it in to try it when GRUB starts during your system startup.  I remember this helped before.

---

