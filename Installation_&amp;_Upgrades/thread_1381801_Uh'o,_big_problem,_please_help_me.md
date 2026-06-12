---
title: "Uh'o, big problem, please help me"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by Hwest on 2010-01-15
Ok, my other OS, Vista started to play up, so i did a system restore, they didn't do anything, so i deleted ubuntu's partition and i am going to reinstall it, but now when i boot, grub says partition not found, so i cant boot into anyhting but this live cd, please help me ;[

---

### Post by Leppie on 2010-01-15
this is because grub installs its shell in the mbr, but all the configuration files are in the linux partition holding the /boot folder.
boot with your livecd, then issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
you will get an warning, just ignore it.

---

### Post by Hwest on 2010-01-15
i do the first one, it goes for a bit, then i get a y/n to install, i go Y, and it then says abort

---

### Post by Hwest on 2010-01-15
i tried again, and it works

---

### Post by Hwest on 2010-01-15
Ok, done, now what?

---

### Post by Leppie on 2010-01-15
reboot, it should boot into your windows system ;)

---

### Post by Hwest on 2010-01-15
Brilliant, works, thanks so much

---

### Post by Leppie on 2010-01-15
you're welcome :)

---

