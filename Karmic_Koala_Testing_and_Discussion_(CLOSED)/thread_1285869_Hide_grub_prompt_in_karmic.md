---
title: "Hide grub prompt in karmic"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scribu on 2009-10-08
So, I was running Jaunty and decided to try Karmic beta, using dual boot. I then removed Jaunty and now I'm left only with Karmic. 

The problem is that each time I boot, I am sent to the grub prompt. I would like to revert to the old behaviour where I'm taken directly to the login screen.

Help?

---

### Post by philinux on 2009-10-08
Have you applied all the current updates?

---

### Post by scribu on 2009-10-08
Yep.

Before updating, in the grub prompt I still had the old Ubuntu 9.04 lines, even though the partition had been deleted. They dissapeared after the last update.

---

### Post by philinux on 2009-10-08
This might help or not ;).
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

Try editing /etc/default/grub

Welcome to the new world.

---

### Post by scribu on 2009-10-08
Thanks Philinux; that put me on the right track.

I found this useful guide: [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275").

---

