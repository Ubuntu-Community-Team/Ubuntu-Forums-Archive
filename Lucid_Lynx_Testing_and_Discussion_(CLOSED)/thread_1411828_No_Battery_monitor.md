---
title: "No Battery monitor?"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by keypox on 2010-02-20
I have the alpha 2 installed, and among other issues the most pressing is no battery monitor/indicter. 

I tried installing on but it said no battery found.  This is on a dell studio 1537

---

### Post by JCoster on 2010-02-22
```
sudo apt-get install --reinstall gnome-power-manager
```

---

### Post by keypox on 2010-03-14
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main gnome-power-manager 2.29.91-0ubuntu5
  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.29.91-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.29.91-0ubuntu5_i386.deb)  404  Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Screw it im doing a partial upgrade.  Which might lead to new install on beta day.  Ubuntu is only for fun nowadays for me anyways...

---

### Post by ahorriblemess on 2010-03-14
That's weird, it worked for me.

---

### Post by Ibidem on 2010-03-15
@keypox:
The fix to the "error 404"-
sudo apt-get update
(your machine is trying to get a version that has been removed because current is 2.29.91-0ubuntu6)

---

