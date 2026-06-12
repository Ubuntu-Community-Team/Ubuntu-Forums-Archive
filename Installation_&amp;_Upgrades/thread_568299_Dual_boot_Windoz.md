---
title: "Dual boot Windoz"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by FreeThePenguin on 2007-10-05
ok, im new to linux and new to the forum.  I have done some searching and didn't find my answers, so here we go.  First off i have ubuntu 7 and currently have XP but wanting to move to vista (keep that in mind)  So my first question is, which do i install first? I have read before that the win/lin dual boot is easier if you load windows from the linux bootloader, however several threads on this forum state that windows should be installed first?  So which is it?  And since I'm planning on upgrading from XP to Vista which would be easer for me when it comes time to update?

---

### Post by Pumalite on 2007-10-05
I would install Vista first, next XP, last Ubuntu.

---

### Post by schnupi on 2007-10-05
its easier if u install vista first and then ubuntu. simply because the windows bootloader would overwrite grub. u can boot from grub into both but with the windows bootloader only into windows.

---

### Post by rsambuca on 2007-10-05
Just upgrade to Vista first - this will overwrite your mbr and install the Vista bootloader.  Then use any linux live cd and re-install grub to the mbr, which will detect the Vista partition.

---

### Post by FreeThePenguin on 2007-10-05
ok, im getting ready to do this now and i dont have vista, so its getting xp temporarily

---

