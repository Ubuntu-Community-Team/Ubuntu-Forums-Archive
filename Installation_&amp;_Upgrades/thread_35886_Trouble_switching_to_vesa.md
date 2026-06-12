---
title: "Trouble switching to vesa"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by trommas on 2005-05-20
I have the classic (so it seems) Ubuntu-freeze problem.
I am completely new to Linux, so bare with me...

Found out that I had to change from nvidia to vesa drive to get things working, so I tried:
*
CTRL+ALT+F1

Login as myself

cd /etc/X11

sudo cp -p xorg.conf xorg.conf.bak

edit xorg.conf 
*
-- Here it tells me that I don't have permission.

So first, is this the best solution? Second, what am I typing wrong?

---

### Post by Xian on 2005-05-20
[QUOTE=trommas]I have the classic (so it seems) Ubuntu-freeze problem.
I am completely new to Linux, so bare with me...

Found out that I had to change from nvidia to vesa drive to get things working, so I tried:
*
CTRL+ALT+F1

Login as myself[/QUOTE]
From this point do this:

```
$ sudo /etc/init.d/gdm stop
$ sudo nano -w /etc/X11/xorg.conf

```
Make your edits as needed then start up GDM:

```
sudo gdm
```

---

### Post by trommas on 2005-05-25
I'm writing this inside Ubuntu!!!!

Thanks a lot!

You have no idea how long I've been trying to get Linux to work on my pc!

When I entered Ubuntu, I got the message: "Failed to initialize HAL". What does this mean?

Also, what can I do to fix my nvidia driver back (from vesa), without killing Ubuntu again?

---

