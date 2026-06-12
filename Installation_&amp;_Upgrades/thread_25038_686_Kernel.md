---
title: "686 Kernel?"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Ubunted on 2005-04-09
I've done some searching and reading up on this topic already, but I'm not sure enough to actually dive in and do it just yet.

Poking through Synaptic, I notice kernel images for 386 and architectures such as amd-k7, 686, etc.

I'm running a P3 in my Ubuntu laptop. If I - this is probably going to sound dumb - deselect the 386 option and select the 686 box (non-SMP), will this install a kernel better suited to my system?

Thanks in advance.

---

### Post by bored2k on 2005-04-09
[QUOTE=Ubunted]I've done some searching and reading up on this topic already, but I'm not sure enough to actually dive in and do it just yet.

Poking through Synaptic, I notice kernel images for 386 and architectures such as amd-k7, 686, etc.

I'm running a P3 in my Ubuntu laptop. If I - this is probably going to sound dumb - deselect the 386 option and select the 686 box (non-SMP), will this install a kernel better suited to my system?

Thanks in advance.[/QUOTE]
 Install the 686 kernel, wich should work great for you like it did here then restart and select it. If everything runs ok, then go ahead and remove 386.

---

### Post by Ubunted on 2005-04-09
So it will give me something similar to a boot menu - one kernel or another?

---

### Post by bored2k on 2005-04-09
[QUOTE=Ubunted]So it will give me something similar to a boot menu - one kernel or another?[/QUOTE]
 The boot menu should show something like
Ubuntu linux kernel 386
Ubuntu linux kernel 686
Windows 3.1 LSD Edition

---

### Post by Ubunted on 2005-04-09
Well it didn't give me any menus, might have been because I selected both the kernel and boot images and it overwrote something, but it went right into 686 mode and seems to be working fine. I removed the 386 components without a hitch. Linux kicks ass - I can only imagine the horror that would be involved if Windows ever had that capability.

Thanks muchly!

---

### Post by bored2k on 2005-04-09
No problem. Weird you didnt get a boot menu. sudo apt-get install grubconf and run it from a root terminal to see if it's hidden. If you dont need it dont activate though.

---

