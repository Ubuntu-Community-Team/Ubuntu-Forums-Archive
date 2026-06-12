---
title: "killed system adding HDD"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by Twig E. Pottox on 2007-12-10
something I did to the fstab file has caused the system to boot to a prompt and it doesn't behave like the terminal. I cant run gedit to undo what i did to fstab. sorry but I am prettly useless at the command prompt.

---

### Post by taurus on 2007-12-10
Gedit won't work if you are not running any window manager.  Therefore, try nano instead.

```
nano -Bw /etc/fstab
```
Then, make whatever changes you need to.  When done, save it with <Ctrl>o and exit with <Ctrl>x.  Then, reboot and see if it boots okay now.

```
shutdown -r now
```

---

### Post by Twig E. Pottox on 2007-12-10
thanks , the system is back up. time to find another how too on adding a HDD

---

### Post by Twig E. Pottox on 2007-12-10
thanks , the system is back up. time to find another how too on adding a HDD

---

