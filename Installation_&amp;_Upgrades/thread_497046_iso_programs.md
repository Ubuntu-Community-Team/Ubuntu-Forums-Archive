---
title: "iso programs"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by mr.farenheit on 2007-07-09
is there a program out there for ubuntu to rip and burn iso images. i mainly wanna try experiment with other versions on linux and such but hate doing it through window's provided softwares.

---

### Post by Matakoo on 2007-07-09
I'm not quite sure what to suggest when it comes to ripping...it rather depends on what you want to rip. For burning an iso, it's installed by default. IIRC, in Gnome (I use KDE myself so the memory might not serve me right) you just right-click on the iso and select Burn to disc or words to that effect. You should find a burner-application in the application menus, and under Places as well.

Otherwise, just download Brasero, K3B (for KDE but works in Gnome too), or Graveman. Either would work well and is available in Synaptic if not installed already. You can do it from the commandline too,  like:

cdrecord 		-v 		-pad dev=/dev/scd0 		src.iso (works on my machine, you may need to change the dev= part on yours)

---

