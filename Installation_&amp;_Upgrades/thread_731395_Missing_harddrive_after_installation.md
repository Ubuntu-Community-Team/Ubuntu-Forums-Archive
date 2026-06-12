---
title: "Missing harddrive after installation"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Paracelsus on 2008-03-21
I just deleted my windows and installed Ubuntu 7.10 and one of my hard drives are missing. I have a total of 4 hard drives 2 external and 2 internal and all of them are showing up except a sata internal drive. It is quite a bit of hard drive space, 160 gigs, and I would like to reacquire it :) Any suggestions?

---

### Post by Pumalite on 2008-03-21
If your OS is Ubuntu, from the Terminal, post:
sudo fdisk -lu

---

### Post by Paracelsus on 2008-03-22
Thanks, I ended up getting it fixed by running Automatix, it had a option to mount all hard drives again in it as write enabled. Works good now :)

---

