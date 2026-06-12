---
title: "Ubuntu installed on UEFI - Problems"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by joao2 on 2014-03-03
First of all a big sorry and a huge thank you.

So I bought a new laptop (Toshiba Satelitte M50-A-110, i5, nvidia external graphic and intel internal) and it came with the dreaded UEFI and windows 8.
Using Linux for more than 1 year and a half, on both work and home computer, I thought I could do a clean install, like usually, from a usb drive which I have converted with unetbootin.

So, as expected, problems happened.
At first I couldnt boot, but since I disable secured boot in the bios, it started to went well.
I managed to install the thing, but everytime I tried to boot it from hard drive it didn't allowed me, instead it just booted from USB and everytime with the options try or install (I'm using Elementary OS). Even when it was installed I had those options.
Also, it started this weird boot from network, but since I enabled wake up on lane on bios it ended :).

Running out ot of options, I ran bootrepair for ubuntu. [HTML]http://paste.ubuntu.com/7023566/[/HTML].

Finally, after I ran the boot repair, it doesn't boot from the USB Drive, even if its set as priority on bios.
All I have is the [HTML]http://i.stack.imgur.com/Hug73.jpg[/HTML].
I have also tried to boot the kernel with the VMLINUZ from there, but it says "object not found" or some error like that (I'm at work now so I don't recall the exact error (if you have more ideas on this please tell me))
I tried on my old broken laptop and I can boot the USB from there.
One more last thing, to just make this a bit more odd, when I enable secure boot from BIOS with USB on priority, I can get to the menu "Install/Try Elementary OS" but if I click on any of them, I just get black screen (I guess it's because its somehow blocked, I used to get this in the past and I only could get into instalation menu after I disabled secure boot)

TL;DR: Tried to install ubuntu on a UEFI computer, after running boot repair all I have is minimal bash.

Thank you very much, after using linux for a few times I never had the need to register and ask, because mostly I could resolve everything by a google search, but now I turn to you guys. Thank you. :(:(:(

---

### Post by joao2 on 2014-03-03
Just changed to legacy boot, everything goes fine, lol. Thanks anyway! You can close this thread

---

