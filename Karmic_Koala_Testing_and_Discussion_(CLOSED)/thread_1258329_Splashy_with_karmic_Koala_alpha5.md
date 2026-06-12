---
title: "Splashy with karmic Koala alpha5"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dkcross on 2009-09-04
Hello dear friends, i have problems with splashy, when ubuntu its starting the message is "splashy connection refused" the how's its [http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709) 


Thanks for all :popcorn:

---

### Post by kestal on 2009-09-05
I could be wrong, but I do not think that Splashy is even possible anymore in Karmic (especially now with xsplash), with what they did with the whole startup processes.

---

### Post by taavikko on 2009-09-05
> **kestal said:**
> I could be wrong, but I do not think that Splashy is even possible anymore in Karmic (especially now with xsplash), with what they did with the whole startup processes.

Usplash will stay onboard as failsafe.

---

### Post by 23meg on 2009-09-05
> **kestal said:**
> I could be wrong, but I do not think that Splashy is even possible anymore in Karmic (especially now with xsplash), with what they did with the whole startup processes.

[SIZE="1"][COLOR="Blue"][citation needed][/COLOR][/SIZE]

---

### Post by dkcross on 2009-09-05
But, any idea for run splashy in karmic?

---

### Post by dinxter on 2009-09-05
i get a few problems,
- splashy conflicts with a file from lsb-base, can be force installed but this is never wise
- with usplash and xsplash uninstalled i get a blank screen on boot up (still boots ok). there was mention somewhere that there could be an issue with udev and splashy startup conflicting in /etc/rcS.d but i havent got round to looking into that and how it works with upstart

i would ask, is setting the vga= option in the kernel bootup line still the preferred method? i thought that might have changed but i might be confusing myself with grub2 changes
i might see if i can tinker with splashy properly early next week

---

