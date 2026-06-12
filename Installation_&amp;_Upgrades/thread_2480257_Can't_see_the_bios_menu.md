---
title: "Can't see the bios menu"
date: 2022-10-23
forum: Installation &amp; Upgrades
---

### Post by eilamigo on 2022-10-23
Hello, I'm having some issues with my Bios.

Yesterday I updated the bios of my motherboard
Gigabyte Technology Co., Ltd. H410M S2H V3
From F1 to F6

The update worked, and it seems like nothing went wrong (I hope), but i not longer have image while starting my bios,

I tried a couple of things

Restart the bios:

I took off the battery of the motherboard and waited a bit, and then screen popped up asking me to configure the bios. I just save the defaults, because I thought that they were working in the moment, save restarted and no more image again, I tried to do it again but it doesn't show the screen anymore.

iI tried to remove the battery again (all plunged off, waited a bit), also using the clear CMOS jumper (again all unplugged, used a screwdriver to make the connection for 5 sec like the manual says to do)

I thought that maybe I installed the bios update wrong but I managed to start ubuntu by just connecting my GPU(for some reason only the  GPU outputs work), my ssd with ubuntu mouse and keyboard

I tried to use boot-repair to see if it did something but it said at the end that it won't do anything, so I guess I need some advanced settings to fix that or not use boot-repair.


different video outputs

I tried using all the video connections I can, all the motherboard and GPU outputs, none of them work, BTW the one time I managed to see the bios screen i was connected to the HDMI of the GPU.

the paste bin of boot repair:
[https://paste.ubuntu.com/p/fgcSsJWQbp/](https://paste.ubuntu.com/p/fgcSsJWQbp/)

Thanks for the help in advance

---

### Post by tea for one on 2022-10-23
> **eilamigo said:**
> I'm having some issues with my Bios.
Yesterday I updated the bios of my motherboard
Gigabyte Technology Co., Ltd. H410M S2H V3
From F1 to F6
The update worked, and it seems like nothing went wrong (I hope), but i not longer have image while starting my bios
Boot-repair is not designed to repair UEFI/BIOS configuration.
Have you tried pressing the Del key when the PC is starting?
[https://www.gigabyte.com/Support/FAQ/81](https://www.gigabyte.com/Support/FAQ/81)

---

### Post by eilamigo on 2022-10-23
And is working, thanks.

---

