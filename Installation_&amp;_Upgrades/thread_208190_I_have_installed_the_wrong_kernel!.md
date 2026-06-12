---
title: "I have installed the wrong kernel!"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by nessus on 2006-07-03
carelessly enough, i blandly installed a 2.6.15-25-386 kernel, what i should have installed should be a 686 kernel i think.
my cpu is AMD 4200X2 dual core.

after a few days of playing around and i noticed constantly 100% CPU usage, and that's how i suspected the problem.

so what i am asking is that, after a search on synaptic, a few things showed up, and here are what i think should be installed instead the current kernel:

linux-headers-2.6.15-25-686
linux-image-2.6.15-25-686

are there anything else i need to add? and how do i go by doing this? just simply mark them and install them as i do for other packages? i know this is a kernel install, and i want to be careful about it. so thats why i am posting this thread to make sure i dont mess up anything again.

thank you!

---

### Post by woedend on 2006-07-03
i think if you just mark the package linux-686 for installation it takes care of everything(restricted modules, image, etc)..You probably will want those restricted modules.
but also mark the headers separately yes, I dont believe they are included.  Dont uninstall the old kernel just in case you have a problem.  If for some odd reason it doesnt want to boot, you can push escape at boot time and select your old kernel.

K7 may be a better choice, but 686 should work just the same.

---

### Post by az on 2006-07-03
[QUOTE=woedend]

K7 may be a better choice, but 686 should work just the same.[/QUOTE]

Actually, I think 686 is a *bad* choicd for and AMD cpu - The k7 kernel is what you want.


sudo apt-get install linux-k7

---

### Post by nessus on 2006-07-03
thx, so k7 then. will try. thank you all!!

---

### Post by nessus on 2006-07-03
ok, it was a little bit trickier than i expected, but luckly i worked out. 
it actually needs linux-restricted-modules to be updated as well. i found out about this after upgraded the kernel and x server stopped working. i chech the log file, it reported "model nvidia not found". i immdiately changed my xorg.conf, change "nvidia" back to "vesa". restarted x server. once i got the GUI back, fired up synaptic, removed old 386 restriced-modeles and installed the k7 one. also just to be in case, i reinstalled nvidia-glx and nvidia-kernel-common. changed vesa back to nvidia, rebooted pc. everything is working now.

ubuntu correctly detect 2 cores in my system now. thank you guys!!

---

### Post by az on 2006-07-03
[QUOTE=nessus]ok, it was a little bit trickier than i expected, but luckly i worked out. 
it actually needs linux-restricted-modules to be updated as well. i found out about this after upgraded the kernel and x server stopped working. i chech the log file, it reported "model nvidia not found". i immdiately changed my xorg.conf, change "nvidia" back to "vesa". restarted x server. once i got the GUI back, fired up synaptic, removed old 386 restriced-modeles and installed the k7 one. also just to be in case, i reinstalled nvidia-glx and nvidia-kernel-common. changed vesa back to nvidia, rebooted pc. everything is working now.

ubuntu correctly detect 2 cores in my system now. thank you guys!![/QUOTE]
If you install the package named "linux-k7", you get everything including the restricted modules packages.  That's what that package is for.

---

### Post by nessus on 2006-07-03
yeah, now i know.
i read the version number of that pkg, i didnt know if it would match.

---

