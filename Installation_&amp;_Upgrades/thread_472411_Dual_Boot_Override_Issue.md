---
title: "Dual Boot Override Issue"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by mrphantastic on 2007-06-13
I finally got Vista and Feisty to dual boot, but now i cannot get the Feisty boot manager to show up at all.  When i restart, nothing.  Windows just shows up.  I push F8, and it's still only Windows options, any ideas anybody?  I wanna have Linux capabilities cuz i hate the resources Vista is chewing up...ugh.

---

### Post by FRuMMaGe on 2007-06-13
> **mrphantastic said:**
> I finally got Vista and Feisty to dual boot, but now i cannot get the Feisty boot manager to show up at all.  When i restart, nothing.  Windows just shows up.  I push F8, and it's still only Windows options, any ideas anybody?  I wanna have Linux capabilities cuz i hate the resources Vista is chewing up...ugh.

Did you install Vista first?  Windows has an annoying habit of hating other partitions if it is not installed first.

I would recommend you boot into Fiesty using your Live-CD and mounting your hard drive (Probably: "mount hda1 /media") then edit your grub config.  I'm not sure where this is, but just search the forum.

---

### Post by mrphantastic on 2007-06-13
Yeah, i got tired of it and just installed them on completely separate HDD'S.  Funny how i had to do that, eh?  Oh well.  Thank you though.

---

