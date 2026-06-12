---
title: "Dapper WinXP duel boot problem"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by birdman on 2006-07-29
I have tried to install Dapper on my system without much joy.
Ubuntu doesnt see the Windows XP installation.  Ubuntu installs OK, but Grub has no Windows option. Can anybody tell me why????

---

### Post by confused57 on 2006-07-29
Open a terminal and post the output of these commands:

```
cat /etc/fstab
```

```
sudo fdisk -l
```
The -l is a small "L".

You'll probably need to add a Windows entry to your
/boot/grub/menu.lst
in order to boot Windows.

---

### Post by birdman on 2006-07-29
Sorry I cant do that beceause I have removed Ubuntu and recovered Windows.  I have tried Fedora 5 without any problems. I then tried it with Ubuntu again and the same thing happened.  I dont feel inclined to try Ubuntu again until I find out what is going on.
My computer has CRITICAL busines data on Windows and I cant risk another failure.

---

