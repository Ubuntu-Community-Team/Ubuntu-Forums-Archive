---
title: "error when installing"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by jh77if on 2010-08-23
I downloaded Ubuntu 10.4 netbook edition for my toshiba satellite a105 laptop (windows XP) burned it to a CD, restarted my computer with the disc in drive, pressed f12 at the appropriate time, chose to boot from CD. after sitting for a second i get error PXE-e61 media test failure, check cable. and then it boots XP normally. how do i get around this to install linux!

---

### Post by clrg on 2010-08-23
Your computer tries to boot from the LAN card. You most likely didn't select the correct boot option. 

Make sure you closed the tray before starting it, and make sure you select the proper boot option. 

If it still doesn't work, go to the BIOS and disable PXE (LAN boot).

---

### Post by jh77if on 2010-08-23
> **clrg said:**
> Your computer tries to boot from the LAN card. You most likely didn't select the correct boot option. 

Make sure you closed the tray before starting it, and make sure you select the proper boot option. 

If it still doesn't work, go to the BIOS and disable PXE (LAN boot).

I selected CD/DVD all 10 times that i've tried so far. tray has been closed. how do i disable PXE? i'm really not so sure that's the problem because i'm choosing to boot from cd/dvd so im not sure as to why my computer would try to LAN boot on its own. but how do i go about doing that,

---

### Post by loren45 on 2010-08-23
> **jh77if said:**
> I downloaded Ubuntu 10.4 netbook edition for my toshiba satellite a105 laptop (windows XP) burned it to a CD, restarted my computer with the disc in drive, pressed f12 at the appropriate time, chose to boot from CD. after sitting for a second i get error PXE-e61 media test failure, check cable. and then it boots XP normally. how do i get around this to install linux!

I just ran into a similar issue today with a Toshiba satellite 100. It wouldn't boot from CD no matter what I did in the BIOS. 

I ended up flashing the bios with an upgraded file from the Toshiba website. After that, when I hold f12, then select the picture of the CD below the Toshiba logo, it finally booted from the disc after several hours of frustration. It has to be done manually every time but it works. 

The install went fine until the reboot when it froze up but thats a different discussion. 

Not sure if that will help you or not but I figured I'd mention it. 

Good luck.

---

### Post by clrg on 2010-08-23
If the BIOS fails to boot from the media you selected, it automatically tries the next in its list.

So if it can't boot from CD, it will try PXE, and then HDD, and so forth.

Check for a BIOS update for your system. If one is available, install it.

---

