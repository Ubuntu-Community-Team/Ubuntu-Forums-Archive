---
title: "black screen after boot help"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by twist2b on 2007-10-03
"Edit /boot/grub/menu.lst, and change all the instances of "quiet splash" to just "splash".
You should be able to boot with recovery mode if you need to."

ok well that was to confusing to me i dont know how to get to that stuff
can anyone give me a step by step instructions on how to do this?
thanks
(yea im no ordinary n00b, more like a super n00b with ubuntu)

---

### Post by taurus on 2007-10-03
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
That's how you edit /boot/grub/menu.lst as root.  When done, save it and exit the gedit window.  Then reboot.

---

