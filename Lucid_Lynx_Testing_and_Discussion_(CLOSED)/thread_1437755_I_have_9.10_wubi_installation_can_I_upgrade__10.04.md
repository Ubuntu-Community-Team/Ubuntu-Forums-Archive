---
title: "I have 9.10 wubi installation can I upgrade  10.04 ?"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hoboy on 2010-03-24
I have 9.10 wubi installation can I upgrade ?
I use dual booting vista ubuntu 9.10.
my computer is a toshiba satelite laptop.

---

### Post by nhasian on 2010-03-24
Yes, you should be able to.

To upgrade from Ubuntu 9.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.04' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by garvinrick4 on 2010-03-24
Yes you can. Any way available nhasian has GUI way which is good or this way. Take your pick.

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by hoboy on 2010-03-24
to upgrade I have used.
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade
But
It seemed like my machine hangs on:
Found linux image: /boot/vmlinuz-2.6.32-17-generic
any suggestion ?

---

### Post by Rody on 2010-03-24
use the recovery boot method from grub and then startx after you log in. Load up your video drivers and it might work, at least it did for me.

rody

---

### Post by hoboy on 2010-03-24
After installation I was asked to restart.
I go automatically to 
Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.
grub rescue>
when I use ls
it show (hd0)
please help
When I launch the computer then press down SHIFT, i get the same error message.
Error: no such device: 8c35181b-d6d0-476f-a1b2-7503d2915da7.
grub rescue>

---

