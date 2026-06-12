---
title: "Upgrade kernel via apt-get"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by Chowchilla on 2012-07-03
Hi all,

I'm attempting to upgrade the kernel in 12.04 via apt-get, which by default has the three relevant packages held back (linux-generic, linux-headers-generic, linux-image-generic). I figured the standard method of unholding packages via dpkg would solve this, so I tried:

```

sudo su
echo "linux-generic install" | dpkg --set-selections
echo "linux-headers-generic install" | dpkg --set-selections
echo "linux-image-generic install" | dpkg --set-selections
exit
sudo apt-get update
sudo apt-get upgrade

```However the packages still remain held back. What am I missing here?

(Note: I want to upgrade the kernel via apt-get from the default source(s), so alternative methods using PPAs, .debs or compiling manually are not what I want)

---

### Post by wojox on 2012-07-03
Run:
```
sudo apt-get update; sudo apt-get dist-upgrade
```

---

### Post by Chowchilla on 2012-07-03
Ha, completely slipped my mind about dist-upgrade. Been too long since I last used apt-get!

---

