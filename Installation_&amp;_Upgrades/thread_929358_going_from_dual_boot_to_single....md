---
title: "going from dual boot to single..."
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by spotsworth on 2008-09-24
hi all,

i've been dual booting gutsy/windows for a while and it's time to put my windows partition to better use(i.e. not just taking up space).  my plan is to format the partition containing windows, but i'm concerned about gutsy booting automatically.  

will i still be prompted to choose what to boot, will it be automatic, or do i have to somehow set it to boot gutsy?

gracias,
spots

---

### Post by iaculallad on 2008-09-24
Are you currently using Gutsy's GRUB to select w/c OS to load at startup? If so, you could just edit your /boot/grub/menu.lst file and remove the entries of your windoze OS.
I don't see any problem if you're booted of Gutsy automatically since you're now going to single booting.

---

### Post by spotsworth on 2008-09-24
I'm not sure.  A screen listing 3 linux kernel and windows xp pops up in a box, and if i don't respond gutsy will boot automatically after 30 seconds...

---

### Post by iaculallad on 2008-09-24
That would be just fine. After formatting your NTFS drive (where windoze xp resides), you have to manually edit the menu.lst file and remove the entries of your xp option. Save and Close the file.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by spotsworth on 2008-09-25
thankyou

---

