---
title: "Add Karmic repo to Jaunty ?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by meijer.o on 2009-09-30
I want to test the x-server of Karmic. Can somebody tell me how to add the Karmic repo to Jaunty?

Thanks a lot,

meijer.o

---

### Post by mac9416 on 2009-09-30
I understand one uses a thing called "apt pinning" to do this. [APT-Pinning for Beginners]("http://jaqque.sbih.org/kplug/apt-pinning.html") should help.

Alternatively, you can just do an early dist upgrade...
```
$ sudo update-manager -d
```

Of course, I have to give the disclaimer: Ubuntu Karmic is still alpha and early dist-upgrades are dangerous, etc.

Good luck. :)

---

### Post by cariboo on 2009-09-30
Karmic beta is out tomorrow, Oct 1, why not download and install it. If you start adding Karmic repositories, you will run into problems with dependencies.

---

