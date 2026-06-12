---
title: "moving ubuntu to second hdd vs. clean install"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by absolutely on 2009-11-17
Howdy
I was wondering what would be better or easier: moving ubuntu to a second hdd or doing a clean install?  I recently installed a second hdd on my brother-in-laws computer.  I had recently introduced them to ubuntu, and they love it, but just needed more space.  I'm not a complete noob, just have no short term memory.  Please help. Thanx in advance

---

### Post by hoare on 2009-11-17
i would just mount the second hdd as /home.
i dont think you can just copy the data and then boot from the other, you would have to change at least  grub...

---

### Post by absolutely on 2009-11-17
That's sounds easy enough. Thanx

---

### Post by audiomick on 2009-11-17
Hallo. I am not sure, but I think just mounting a new disc as home might confuse your system. If you are only trying to add more space and nothing more, I would mount the new disc at a point within home. That will not confuse anything; the file system is conceived such that this is "normal procedure"
For your information, the partitions on my computer that don't "belong" to the actual installation turn up in /media

---

