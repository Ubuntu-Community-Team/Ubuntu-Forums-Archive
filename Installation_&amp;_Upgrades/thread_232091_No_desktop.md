---
title: "No desktop"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by Nixforce on 2006-08-08
Hi there,

I have installed Ubuntu 5.04 on my Microsoft Virtual Server, but it boots up with out a desktop, how can i get a desktop on it?

---

### Post by Jagot on 2006-08-08
Did you install the server version?  Can you see the command line?  If you can, then do this:

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

Is there any reason you don't want to use Dapper?

---

### Post by Nixforce on 2006-08-08
It seems to be installing/the desktop.. Im installing 5.0.4 as my first test of ubuntu,Ive got 6.06 LTS, but not sure on the installation of that, will try on another vps

---

### Post by Nixforce on 2006-08-08
Hi, I did all that, but the desktop does not show, how can i get it to start automatically?

---

### Post by Jagot on 2006-08-08
Try this:

```
startx
```

---

### Post by Nixforce on 2006-08-09
I just watched the boot up, I did a screen shot of the error, how do i solve this?

---

