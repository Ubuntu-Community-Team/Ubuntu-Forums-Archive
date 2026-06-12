---
title: "Kernel changed to Kali Rolling Linux"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by tessalz on 2016-07-28
Good day Ubuntu family, I was trying to do a sudo apt-get upgrade yesterday on my system, and the upgrade wasninterrupted and I had to restart my system, upon restarting I was unable to boot into Ubuntu again. So I switched over to console from the blank screen and resumed the upgrade,  when the upgrade was completed I then restarted my pc with hope that it should be back to live, to my surprise in grub load I saw Kali Linux kernel. How is this even possible and still am unable to login into Ubuntu still stuck at a blank screen. Please help have got lot of stuff on my pc

---

### Post by CantankRus on 2016-07-28
Enabled repositories?
Post the terminal out of...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

