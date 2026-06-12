---
title: "UNR: Trackpad tap not working"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by blazemore on 2009-06-14
On Ubuntu Netbook Remix 9.10, the trackpad tap on the Aspire One does not emulate a mouse click.
The option is turned on in Properties->Mouse

Also, the scrollwheel section of the trackpad doesn't work as a scrollwheel. Similar problem.

---

### Post by mc4100 on 2009-06-14
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391)

---

### Post by MacUntu on 2009-06-14
Can we have a stickie please? Seems this bug gets a new thread every day. :D

---

### Post by Vanishing on 2009-06-14
this problem can be solved by installing gsynaptics.
do:
> sudo apt-get install gsynaptics

after installation, go to System>Preference>TouchPad
Then in general tab, enable tap.
There you go.

---

### Post by TwiStEr55 on 2009-06-16
thank you :P

---

