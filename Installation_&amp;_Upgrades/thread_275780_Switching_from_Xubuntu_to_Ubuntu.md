---
title: "Switching from Xubuntu to Ubuntu"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by zergberg on 2006-10-11
I got a new, more powerful computer, so I figured I'd try out GNOME. How do I install all the ubuntu-desktop stuff from the Dapper CD? I tried to add it to apt, but now I simply have no packages. (I also commented all my other repositories to prevent apt from downloading the updated packages over dialup.)

---

### Post by taurus on 2006-10-11
If you have network connection, download and install Gnome on your machine with

```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```
And if you want to add your CD to /etc/apt/sources.list, then do

```

sudo apt-cdrom add

```

---

### Post by zergberg on 2006-10-11
I have added the CD, and it's there, but I can't get any packages from it.

---

### Post by newmonkey on 2006-10-11
Do you have to install it from the CD?

why not```
sudo apt-get install ubuntu-desktop
```

---

### Post by zergberg on 2006-10-11
I'd rather not, I have dialup and it would take about a week :(

---

### Post by aysiu on 2006-10-12
You won't be able to install it off the **Desktop CD**.

If you want to install it from CD, you have to use the **Alternate CD**.

Do you have the Desktop or the Alternate?

---

