---
title: "how large should root partition be"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by john5898 on 2008-09-14
ya

---

### Post by Pumalite on 2008-09-14
10-15 gb

---

### Post by rpm13 on 2008-09-19
Ive been running with root at 700M and boot at 100M
(ie 0.7G and 0.1G).
That of course implies that you have /usr /var and /home (at the least) separated. These could go as low as
/usr: 2G
/var: 1.5G
/home: whatever!

But with this arrangement ubuntu had trouble upgrading: update-manager downloads into /boot and then fails if theres not enough space -- a stupid choice if you ask me.  But if /boot is merged with root (/) at about 1G that should be fine.

---

### Post by jerome1232 on 2008-09-19
As rpm is kinda getting to that all depends on your partitioning scheme,

if you partition out /home, /var, /boot, /usr then root could be around 100 - 200 MB

/var; /usr; and /home seem to be the big space eaters.

If you go the common method of having a / and a /home then
/ 12-20 GB depending on how many programs you install (programs usually go to /usr)
/home The rest of the drive (this is implying that you keep all of you multemedia here)


In my case I have

/ 15 GB
/boot 2 GB
/home 15 GB
/mnt/data The rest of the Drive

---

### Post by Sef on 2008-09-19
Ubuntu recommends 8 - 10 GB with a separate home parition.

---

### Post by Pumalite on 2008-09-19
I agree. Root, home and swap should do it.

---

### Post by Vivaldi Gloria on 2008-09-20
I prefer

/ - 15GB 
swap - your ram x 1-2
storage partition - rest

I mount the storage partition in /mnt/mountpoint and put a symlink in home or where ever I want. I prefer a storage partition over a /home partition because I like having new config files when I install a new system.

---

