---
title: "Remove kubuntu-desktop from kubuntu and install ubuntu"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-08-27
Hi. 
I am using kubuntu karmic 64bit and i uninstalled kubuntu-desktop and installed ubuntu-desktop

Before that i've been trying to make gdm the default display manager

by this

```
sudo dpkg-reconfigure gdm

```
but i always got the below output

```
Reloading GNOME Display Manger configuration...
 * Changes will take effect when all current X sessions have ended.
 invoke-rc.d: initscript gdm, action "reload" failed."
```

i tried the same @ root in recovery mode and i always get this..

and if is ```
sudo /etc/init.d/gdm start
```

```
Not starting GDM: it is not the default display manager
```

any help?

here there seems to be a solution 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483433](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483433)

i don't what splashy is..

thankyou

---

### Post by taavikko on 2009-08-27
Edit /etc/X11/default-display-manager file
if /usr/bin/kdm -> /usr/sbin/gdm

---

### Post by n3had on 2009-08-27
> **taavikko said:**
> Edit /etc/X11/default-display-manager file
if /usr/bin/kdm -> /usr/sbin/gdm

i did it right away .. will reboot now

and yeah it was kdm..

---

### Post by n3had on 2009-08-27
> **taavikko said:**
> Edit /etc/X11/default-display-manager file
if /usr/bin/kdm -> /usr/sbin/gdm

```
usr/bin/kdm -> /usr/**sbin**/gdm
```

i had fixed everything weeks back. But was blinded to see the above command in bold lol. i always tried /usr/bin/gdm.. thanks again.. really appreciated .. nice to see DEFAULT GDM! :P

---

