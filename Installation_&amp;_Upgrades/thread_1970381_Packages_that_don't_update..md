---
title: "Packages that don't update."
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by chrispche on 2012-05-01
[[img]http://i45.servimg.com/u/f45/11/95/68/21/screen10.jpg[/img]](http://www.servimg.com/image_preview.php?i=49&u=11956821)

If you look at the screenshot there is two items that refuse to upgrade or go away. Any ideas? I upgraded from 11.10 over the air. I'm using the 64bit version of 12.04.

---

### Post by tomatoe on 2012-05-01
Have you tried upgrading from terminal?

---

### Post by chrispche on 2012-05-01
No I have not. Do you have the command handy?

---

### Post by chrispche on 2012-05-01
I used sudo apt-get dist-upgrade. I got:

> chrispche@chrispche-VGN-AR51M:~$ sudo apt-get dist-upgrade
[sudo] password for chrispche: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ibus-hangul nabi
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
chrispche@chrispche-VGN-AR51M:~$

---

### Post by tomatoe on 2012-05-01
Dist-upgrade is for upgrading from 11.10 to 12.04 for example.

Try 
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by oldos2er on 2012-05-01
> **tomatoe said:**
> Dist-upgrade is for upgrading from 11.10 to 12.04 for example.


No, apt-get dist-upgrade allows apt-get to install new packages instead of only upgrading current packages (which is what a normal upgrade does). [Thanks, CharlesA]

---

### Post by chrispche on 2012-05-01
Well I'm still getting the same thing.

```

chrispche@chrispche-VGN-AR51M:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ibus-hangul nabi
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
chrispche@chrispche-VGN-AR51M:~$
```

---

### Post by chrispche on 2012-05-01
Solved, manually upgrade using Synaptic Package Manager. Cheers for the help though.

---

