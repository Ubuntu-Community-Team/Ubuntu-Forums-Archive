---
title: "multiple kernels in GRUB menu"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by normanecker on 2008-06-24
My GRUB menu has the following options for booting:

------------------------------------------
Ubuntu 8.04, kernel 2.6.24-19-generic
Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

Windows NT/2000/XP
------------------------------------------

Is it possible to run multiple desktop environments in this way?

---

### Post by llama320 on 2008-06-24
by multiple desktop environments, do you mean GNOME vs KDE vs XFCE vs etc,etc,etc? if so, then...

the kernels listed will work with each environment, though you'll probably want to use the most up to date kernel

You can install KDE over GNOME or whatever you like..but I don't think the kernels will help you to that end

If you do want to install KDE check out the site below:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Good Luck and apologies if I just told you stuff you already knew

---

### Post by normanecker on 2008-06-24
So I can reconfigure one of those kernels to use KDE, and still use Gnome on the other?

---

### Post by llama320 on 2008-06-24
> So I can reconfigure one of those kernels to use KDE, and still use Gnome on the other? 

While I may be wrong, I don't think it's possible to do that, nor would you really want to. The kernel has important security updates that you'll want, but you can boot into an older kernel if the newer kernel has made some change that renders your computer inoperable (unlikely, but it happens)

If you want to try out KDE, you can download it
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

Then (after rebooting), when you hit the login screen you can go to options > select session > KDE and just boot into KDE. for a more in-depth look at all that check out the link I posted earlier :)

---

