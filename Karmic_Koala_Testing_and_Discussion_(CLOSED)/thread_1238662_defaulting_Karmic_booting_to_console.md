---
title: "defaulting Karmic booting to console"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-12
Hi!

(Kubuntu) Karmic is in use (up to date). I have tried to find a way to prevent X (more strictly, kdm) loading after power on. All refs wrt default run level I have found deal with /etc/inittab or /etc/event.d, but these ones don't exist at all in Karmic installation.

Please, point me to right direction to further digging in.


Another small question (related to booting) is: in grub I have  disabled 'splash' and 'quiet'. All is OK (I see loading process), but at some point 80x25 console changes to something with higher resolution. Where is this behavior is configured? I'd want to stay with 80x25.

---

### Post by louieb on 2009-08-12
Heres the  Karmic Discussion Section of the forum [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359).

Haven't played with it much but in earlier versions System>Services un-checking GDM will  keep x from starting.

---

### Post by ilna on 2009-08-12
> **louieb said:**
> Heres the  Karmic Discussion Section of the forum [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359).

Haven't played with it much but in earlier versions System>Services un-checking GDM will  keep x from starting.I haven't GDM at all as far as I use Kubuntu :-)

---

### Post by louieb on 2009-08-12
:confused: Ok KDM. :oops:

---

