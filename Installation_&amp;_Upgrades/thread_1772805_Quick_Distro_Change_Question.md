---
title: "Quick Distro Change Question"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by GeissT on 2011-06-01
Hey,

This is probably a stupid question to ask the Ubuntu Forums, but say if I were to switch from Ubuntu to something such as Mint, could I simply install Mint over Ubuntu and install the bootloader on the 'partition' that GRUB is installed on?

Thanks guys and gals,

GeissT

---

### Post by satanselbow on 2011-06-01
Simple answer... yep.

The stupid questions are the ones you don't ask :D

If you point your new distro's GRUB at the same previously used MBR / partition it will overwrite the existing one so no problem there ;)

If you have a separate /home partition you can also just point the new installer to reuse it BUT DO NOT FORMAT - have a tidy up of (hidden) config files under /home from a liveCD 1st though to prevent config problems on your new machine ;) .mozilla /.thunderbird profiles etc can stay and will be picked up automatically ;)

---

### Post by GeissT on 2011-06-01
Thank you so much, does Ubuntu auto install the boot loader to the same partition as / ?

If so then thats easy then, and it wont matter if i dont remove the .mozilla files? For example if i want to keep my settings?

GeissT

---

### Post by GeissT on 2011-06-01
I will also add that I have GRUB set to dual-boot with windows xp.

---

### Post by TBABill on 2011-06-01
> **GeissT said:**
> Thank you so much, does Ubuntu auto install the boot loader to the same partition as / ?
 
If so then thats easy then, and it wont matter if i dont remove the .mozilla files? For example if i want to keep my settings?
 
GeissT If you want to keep your settings then you must have a separate /home partition. If you do not then the Mint install will overwrite your current /home partition, which is where all those goodies reside. As stated before, install Mint to the SAME partitions (same /, same /home) as you have Ubuntu and do not format /home and you should be fine. One caveat....make a backup of anything important in case either you or the install does something wrong.

---

### Post by GeissT on 2011-06-02
Thanks to both of you,

I will do the install now, if i have any issues ill post back here.

GeissT

---

### Post by asrman on 2011-06-02
Dear all,

I suddenly realized that my linux system is case insensitive.

Is there any way that I can make it case sensitive?

Many thanks.

Bruce

---

### Post by I'mGeorge on 2011-06-02
> **GeissT said:**
> Hey,

This is probably a stupid question to ask the Ubuntu Forums, but say if I were to switch from Ubuntu to something such as Mint, could I simply install Mint over Ubuntu and install the bootloader on the 'partition' that GRUB is installed on?

Thanks guys and gals,

GeissT

sure it depends of how you have installed ubuntu in the first place. If you've made mount points for home folder or other specific folders than they will remain. That's the main idea of having the possibility creating mount points.

---

