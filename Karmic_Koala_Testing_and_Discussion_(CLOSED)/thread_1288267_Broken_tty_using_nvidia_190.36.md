---
title: "Broken tty using nvidia 190.36"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hype on 2009-10-11
Hi there,
i'm using karmic 64bits up to date (kernel 2.6.31-13).
I also use latest nvidia beta driver 190.36.

If i try to switch to tty1 (or any other), i get a screen full of random colors, "noise", which makes tty unusable. Event tho if i type my login and password, and type commands and hit "enter", it works.

I'll try older nvidia driver 190.32 to check if its linked to the driver or not.

Just wondering if anyone had this kind of issue recently, and what version of nvidia driver you use. :D
 Cheers.

---

### Post by anagor on 2009-10-11
I'm using the same karmic 64bit, but with the supplied nvidia 185.18.36 drivers.
And I too have the random noise on TTYs.
I've found this bug:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/448592](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/448592)
which we both probably encountered, but it seems that it's not limited to nvidia drivers.

---

