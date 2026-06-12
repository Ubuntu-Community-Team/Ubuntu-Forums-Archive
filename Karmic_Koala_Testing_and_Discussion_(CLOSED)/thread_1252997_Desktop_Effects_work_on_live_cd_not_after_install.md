---
title: "Desktop Effects work on live cd not after install"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DSn0wMan on 2009-08-29
I think it has something to do with which driver is selected, but with 9.10 I don't seem to have an xorg.conf file anymore so I am not sure how to select a driver, or see which one I am using

---

### Post by TeoBigusGeekus on 2009-08-29
Hardware specs?

---

### Post by DSn0wMan on 2009-08-29
ATI Radeon Mobility 300M. It has worked really well in the past with the radeon driver.

---

### Post by TeoBigusGeekus on 2009-08-29
> **DSn0wMan said:**
> ATI Radeon Mobility 300M. It has worked really well in the past with the radeon driver.
Both intrepid and jaunty?

---

### Post by DSn0wMan on 2009-08-29
Yes. I know Xserver has changed quite a bit in 9.10 can you still use dpkg-recongifure xserver-xorg?

dpkg-recnfigure xserver-xorg does not seem to  do anything.

---

### Post by DSn0wMan on 2009-08-29
Bump!

---

### Post by NoaHall on 2009-08-29
System -> Admin -> Hardware Drivers.

xorg.conf is in /etc/X11/xorg.conf

---

### Post by DSn0wMan on 2009-08-29
> **NoaHall said:**
> System -> Admin -> Hardware Drivers.

xorg.conf is in /etc/X11/xorg.conf

Aparently not in 9.10

josh@josh-laptop:~$ ls -ltr /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

also nothing shows up in hardware drivers, but I do have the newest radeon(open source) driver installed which is what my card usually likes best.

---

### Post by DSn0wMan on 2009-08-29
Looks like I ran into a bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400014](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400014)

rmmod i915 fixed it for me

---

### Post by overdrank on 2009-08-29
Moved to Karmic Koala Testing and Discussion

---

