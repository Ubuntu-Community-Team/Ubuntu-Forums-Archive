---
title: "error22: partition doesn't exist"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by benny999 on 2007-09-02
ok i do a fresh install of ubuntu reason i formatted my ubuntu partition is i wanna start a fresh ultimate version and i get a error when i dual boot on grub when i select ubuntu it says error22: partition doesn't exist after a install and when i go to do the upgrade on the cd it says you have to do this after a hard drive install i also tried just putting the normal ubuntu i downloaded off the net but still the same error

---

### Post by Pumalite on 2007-09-02
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by benny999 on 2007-09-02
thank you that fixed my problem it was trying to boot off hd2,2 when it's hd0,2 now just gotta figure out how to save it

---

### Post by benny999 on 2007-09-02
in grub when i change the root thingy in the ubuntu boot setup from hd(2,2) to hd(0,2) how do i save it

---

### Post by Pumalite on 2007-09-02
Re-install Grub with this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by merlinus on 2007-09-02
You can also edit /boot/grub/menu.lst and change all of the instances of (hd2,2) to (hd0,2).

```

gksudo gedit /boot/grub/menu.lst

```

-merlin

---

### Post by benny999 on 2007-09-03
thanks very much for ur help i edited my menu file (y)

---

### Post by merlinus on 2007-09-03
Glad to help, and that it worked for you.

-merlin

---

