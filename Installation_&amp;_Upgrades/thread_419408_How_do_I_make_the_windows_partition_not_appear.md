---
title: "How do I make the windows partition not appear?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by fructose on 2007-04-23
Ok, I went through the pains of getting my wireless working (needed to re-install in the end) but that un-did something I had done.  I made it to the windows partition wouldn't show up on the 'Computer' in the Places menu.  I don't have any need to access that partition and I would like to make it so I can't see it again.  I read it somewhere before, but I can't find it again.  Can someone please help me out?

Thanks in advance.

---

### Post by mhansen on 2007-04-23
cat /etc/fstab and paste the results please.  Or, save yourself that step and remove the line that refers to your windows partition and it won't be mounted anymore on boot-up.


Regards,
Mike

---

### Post by fructose on 2007-04-23
Ok, I took the lines out, but they are still showing up in the Places list.

---

### Post by mhansen on 2007-04-23
Even after a reboot?


Regards,
Mike

---

### Post by fructose on 2007-04-23
Yes, even after re-boot.  That puzzles me.

---

