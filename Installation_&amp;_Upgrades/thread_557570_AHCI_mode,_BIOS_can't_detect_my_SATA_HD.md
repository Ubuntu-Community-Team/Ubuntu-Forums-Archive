---
title: "AHCI mode, BIOS can't detect my SATA HD"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by fairlady350z on 2007-09-22
I installed Ubuntu and did a dual boot with Vista.
The installation went very well.

The only problem is that when i switch back to AHCI, for some reason BIOS can't detect the HD (Sata).
When I switch it back to IDE, it went ok until loading Ubuntu.
Somehow the screen freezes, I only see Ubuntu logo with that loading bar that doesn't even move.

When I do the recovery mode, this is the last message I got:

Ata6: failed to recover some devices, retrying in 5 secs.

Any ideas?


Thanks

---

### Post by Pumalite on 2007-09-22
Post:

sudo fdisk -lu

---

### Post by fairlady350z on 2007-09-22
i sincerely appologize but can you please tell me how to input sudo?
thanks alot

edit: i tried esc while loading ubuntu but it crashed and boot up from bios again.

---

### Post by Pumalite on 2007-09-22
Applications>Accessories>Terminal

---

### Post by fairlady350z on 2007-09-23
Sorry if I wasn't very clear.
I can't even get into Ubuntu.
During the loading screen (with the loading bar) it freezes.
Nothing happen, after a while I got the message saying something about Job control turned off.

I did a bit of research, and tried to access the grub by pressing ESC when UBUNTU is loading, but that even make things worse. Suddenly it stops and boots from the BIOS again.

So I'm going to try reinstalling it with Kubuntu alternate installer. The ubuntu ultimate seems doesnt work for me.
Even the Ubuntu altrenate also freezes when it reaches 75%.
I hope I would get some luck with Kubuntu.

---

### Post by fairlady350z on 2007-09-23
Doing a clean install solves my problem.

thanks

---

