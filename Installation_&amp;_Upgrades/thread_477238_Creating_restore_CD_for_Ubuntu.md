---
title: "Creating restore CD for Ubuntu?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2007-06-18
Which program is best to create a restore CD for your Ubuntu system? I mean a CD from which you only have the very basic default Ubuntu, but with a few modification like a different loginscreen, Direct rendering fixed etc.
Please don't say use ghost cause that's not what I want. It's sorta a remastered Ubuntu I want, but with my own stuff.
How hard is that to do?

;)

---

### Post by sickpuppet on 2007-06-18
Hi flodis - 

Why not just boot up off the Ubuntu 7.04 live CD?

I'm not clear exactly what the purpose of your restore CD is - describe what you want to be able to do with it.

regards
Ben

---

### Post by Jaxilian on 2007-06-18
> **sickpuppet said:**
> Hi flodis - 

Why not just boot up off the Ubuntu 7.04 live CD?

I'm not clear exactly what the purpose of your restore CD is - describe what you want to be able to do with it.

regards
Ben

You know the installation CD that you can download? I want to be able to sorta modify that one and make so my ATi card is already configured and lets say changed splashscreen and loginscreen and maybe some other stuff.

An installation CD that is customized to my computer in other words.

---

### Post by 00arthuryu on 2007-06-19
i tend to use tar and just replace all my settings and files to a previous state
```

sudo su
cd /
umount -a
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```
then you can put it on a cd or something
and to restore it
```

tar xvpfz backup.tgz -C /

```
Regards :D
A.M.Y.

---

### Post by Jaxilian on 2007-06-19
is there no way to do a custom Ubuntu installation CD?

---

### Post by Jaxilian on 2007-06-24
bump

---

### Post by mburris on 2007-06-30
bump

---

