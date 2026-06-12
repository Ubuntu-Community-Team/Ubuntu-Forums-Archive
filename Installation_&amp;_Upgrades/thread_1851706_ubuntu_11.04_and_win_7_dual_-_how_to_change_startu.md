---
title: "ubuntu 11.04 and win 7 dual - how to change startup timer ?"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by rishi_singh on 2011-09-28
When i start my laptop, i have to choose which OS to boot. The timer allows only 10-15 seconds. How do i increase the time ? Better, how do i switch off that timer ?

---

### Post by haqking on 2011-09-28
> **rishi_singh said:**
> When i start my laptop, i have to choose which OS to boot. The timer allows only 10-15 seconds. How do i increase the time ? Better, how do i switch off that timer ?

You need to edit your grub

```
gksudo gedit /etc/default/grub
``` or whatever editor you prefer


and change the following line:

```
GRUB_TIMEOUT=x
``` to whatever time you want x to be in seconds

```
sudo update-grub
```

see here for more info [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by rishi_singh on 2011-09-29
Thanks ! :) Dont know what those commands mean, but they work. It was the only thing i managed to do so far. My other problems with linux still persist.

---

### Post by haqking on 2011-09-29
> **rishi_singh said:**
> Thanks ! :) Dont know what those commands mean, but they work. It was the only thing i managed to do so far. My other problems with linux still persist.

well surely by carrying them out you know what they mean now.
You opened a file
you made some changes to it
your changes were reflected by achieving your goal

As for other problems, without problems we would never learn ;-)

Glad i could help

cheers

---

