---
title: "How to Upgrade from 9.10 to 10.04 (from ISO)"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zackiv31 on 2010-04-22
I've downloaded the RC... how do i upgrade from my 9.10 install to 10.04 RC?  I've mounted the ISO but don't know how to upgrade.

If that's not possible, how can I upgrade from terminal?

---

### Post by jaco223 on 2010-04-22
> **zackiv31 said:**
> I've downloaded the RC... how do i upgrade from my 9.10 install to 10.04 RC?  I've mounted the ISO but don't know how to upgrade.

If that's not possible, how can I upgrade from terminal?


There are a couple of ways you can approach it. You can go to System>Administration>
Software Sources and add the the cd you burned, then go to System>Administration>
Update Manager. I'm thinking though when you  put the cd in it should recognize you
have luicd and automatically ask you to upgrade.

Or you could upgrade from a terminal, first you'd have to update your /etc/apt/sources.list file with the repositories for lucid. I'll attach my sources.list file for you. Use Gedit or Nano to edit your file.
```

sudo nano /etc/apt/sources.list or
sudo gedit /etc/apt/sources.list
```Then you would do 

```
sudo apt-get update
sudo apt-get -f dist-upgrade
```That should work for you.

Hope this helps.

Jaco

---

### Post by jaco223 on 2010-04-22
Here's the sources file

---

### Post by zackiv31 on 2010-04-22
I tried to use my CDROM... but I have a laptop without one... and it won't let me use a loopback device for a source... that's not cool.

---

### Post by zackiv31 on 2010-04-22
On my way to updating by option #2.  Thanks!

---

### Post by jaco223 on 2010-04-22
> **zackiv31 said:**
> I tried to use my CDROM... but I have a laptop without one... and it won't let me use a loopback device for a source... that's not cool.

Then you could always go the terminal route with the instructions and file I posted.
It's pretty painless actually.

Edit. If you have trouble opening the file I posted, just right click on the link and save as a .txt file

Hope this helps.

Jaco

---

