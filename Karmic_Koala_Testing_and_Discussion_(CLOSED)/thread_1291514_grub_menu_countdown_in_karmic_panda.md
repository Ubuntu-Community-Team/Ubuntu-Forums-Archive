---
title: "grub menu countdown in karmic panda"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Xander {MP} on 2009-10-14
where did they move the menu.lst script inside the grub folder. I want to extend the countdown at the grub menu, but I can't figure out how to do it in karmic panda.

Thx,

Xander {MP}

---

### Post by drs305 on 2009-10-14
> **Xander {MP} said:**
> where did they move the menu.lst script inside the grub folder. I want to extend the countdown at the grub menu, but I can't figure out how to do it in karmic panda.

Thx,

Xander {MP}

The file structure for GRUB 2 is almost completely different from GRUB. It would be to your benefit to review some of the major differences. Take a look at this link. It covers what you want to know:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

Hint: Look in /etc/default/grub. Once you make the changes, run the second command or the changes won't take effect.
```

gksu gedit /etc/default/grub
sudo update-grub

```

Welcome to GRUB 2!

---

### Post by oldfred on 2009-10-14
Its Karmic Koala 9.10:). It now uses Grub2 (1.97 beta3 currently) and it has a whole different layout. Each time you do a update-grub2 it builds a entirely new grub.conf kinda like the automagic area in menu.lst. All the parameters come from separate files that were like the comments at the top of menu.lst or the things you want to manually add.

Grub2 gets its time out information and sets up a hidden menu for you in /etc/default/grub.
   
One of many sites discussing the new grub2
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

I see drs305 beat me to it.

---

### Post by Xander {MP} on 2009-10-14
Karmic Koala :).

---

### Post by Xander {MP} on 2009-10-14
I have been reading up, and what I understood was that all I have to do to get the memtest to not appear is to change the permissions on one of the files.

---

### Post by drs305 on 2009-10-14
> **Xander {MP} said:**
> I have been reading up, and what I understood was that all I have to do to get the memtest to not appear is to change the permissions on one of the files.

For your default partition, all you have to do is make 20_memtest86+ non-executable. To do that, run:
```

sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

```

If you have other partitions with linux kernels, this won't cover them and you would have to do some tweaking. In that case, visit this guide: 
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

---

