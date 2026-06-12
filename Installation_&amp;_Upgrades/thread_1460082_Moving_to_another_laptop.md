---
title: "Moving to another laptop"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by sandsjh on 2010-04-22
Greetings. I searched for "moving to another laptop" and did not find anything, so at least give me credit for searching.

Is Is there a way to backup my current 9.10 NBR isntall and transfer it to the Lenovo? I am moving from a Dell E6500 to a Lenovo T510.

I know how to use Acronis Universal Restore for WinBlows, but not sure how to go about this. 

The way I was looking at is to write down the programs I installed and copy my /home/ to an external drive.

Regard,
Jason

---

### Post by Lepy on 2010-04-22
Either use and external HDD and gparted to copy the partition, or 
run:
```
dpkg --get-selections > ~/packagelist.txt
```

then back up your home folder, install ubuntu on new system, and restore home folder, then run

```
sudo dpkg --set-selections < ~/packagelist.txt && sudo apt-get dselect-upgrade
```

That should do it. Read up on dpkg in any case.

---

### Post by 2hot6ft2 on 2010-04-22
This may be just what you're after. Or at least a easy way to do what you want to do. It was created by lovinglinux a long time forum member.
[http://lovinglinux.megabyet.net/?page_id=534](http://lovinglinux.megabyet.net/?page_id=534)

---

### Post by sandsjh on 2010-04-23
Much appreciated for your answers and time.

Warm regards,
Jason

---

