---
title: "Quadrapassel crashes X"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rob2687 on 2010-03-27
In Quadrapassel set the Starting level sufficiently high (i.e. level 20) so that the bricks will fall fast and end the game quickly. Exit Quadrapassel and X will crash when the window is about to close and throw a bunch of errors in Xorg.0.log.

Sometimes it takes a couple of tries of the above procedure to crash X but it is guaranteed to crash X (almost) everytime I run through these steps.

I don't know if this is actually the case but it seems like holding down the right or left arrow while the bricks are falling also ensures that it will crash X when closing the game.

Can anybody duplicate this?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/549576](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/549576)

---

### Post by MartinuxP on 2010-04-01
Hi,

In my lucid installation when i close Quadrapassel the X session close and I have do log in again (all programs closed...)

---

### Post by happyhamster on 2010-04-01
The crash is related to the libclutter library: either wait until those packages get fixed, or manually downgrade libclutter and libclutter-gtk to libclutter-1.0-0_1.0.6-0ubuntu1 and libclutter-gtk-0.10-0_0.10.2-0ubuntu2. (In case you really can't do without Quadrapassel that long :) )

[https://launchpad.net/ubuntu/lucid/+package/libclutter-1.0-0](https://launchpad.net/ubuntu/lucid/+package/libclutter-1.0-0)
[https://launchpad.net/ubuntu/lucid/+package/libclutter-gtk-0.10-0](https://launchpad.net/ubuntu/lucid/+package/libclutter-gtk-0.10-0)

---

### Post by MartinuxP on 2010-04-05
Quadrapassel is my life!!! :D

Anyway with the rev. 17 of the kernel this bug doesn't exist, with release 15 it's as I've described before.

---

