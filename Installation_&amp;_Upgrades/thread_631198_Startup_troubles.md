---
title: "Startup troubles"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by mikewujcik on 2007-12-04
My video card went kaput and I had to change it. I have Ubuntu 7.10. It was working perfectly until the card was changed. Now when I startup, it reaches the first Ubuntu splash screen and then goes into terminal mode to login and password. I do not know how to bring  the Gnome desktop back up and make it the default instead of terminal. I hope I am making sense. I decided if I were to learn Linux, I would have to remove Windows completely and rely on Linux. I am not computer illiterate but am brand new to Linux, so any help will be appreciated.

---

### Post by Pumalite on 2007-12-04
It looks like you have to reconfigure your xserver.
sudo dpkg-reconfigure xserver-xorg

---

### Post by mikewujcik on 2007-12-04
Thanks, Pumalite, that did the trick. I am amazed at the quick responses on this forum.

---

### Post by Pumalite on 2007-12-04
You are welcome. Good luck.

---

