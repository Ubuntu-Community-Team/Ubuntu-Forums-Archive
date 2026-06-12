---
title: "If KDM is installed, the new GDM can never be made default again..."
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-07-20
Is this supposed to happen?

---

### Post by wayne_cat on 2009-07-20
edit the file:

/etc/X11/default-display-manager 

```
oot@macbook:~# cat /etc/X11/default-display-manager 
/usr/sbin/gdm

```

---

### Post by vegetarianshrimp on 2009-07-20
In the terminal, type:
> sudo gedit /etc/X11/default-display-manager
This will open a file.
erase all lines in the file, and replace them with only one line:
> /usr/sbin/gdm

---

### Post by Starks on 2009-07-20
Heh. That wasn't working before. It works now though.

Maybe the update fixed it.

---

### Post by vegetarianshrimp on 2009-07-20
> **Starks said:**
> Heh. That wasn't working before. It works now though.

Maybe the update fixed it.
Glad we helped.

---

### Post by MacUntu on 2009-07-20
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591)

---

### Post by Starks on 2009-07-20
I wasn't even able to get the picker to show up when running the dpkg-reconfigure command.

---

### Post by wayne_cat on 2009-07-20
> **Starks said:**
> I wasn't even able to get the picker to show up when running the dpkg-reconfigure command.

does not work at the moment. ;)

---

