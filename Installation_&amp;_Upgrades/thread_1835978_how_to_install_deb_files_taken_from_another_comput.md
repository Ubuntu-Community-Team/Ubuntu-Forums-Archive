---
title: "how to install deb files taken from another computer"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by aronin on 2011-08-30
I've installed ubuntu 11.04 .but i  don't have an internet connection. I have these deb files taken from my friends computer (from /var/cache/apt/archives).please help me to install this files without any dependency problem.

---

### Post by collisionystm on 2011-08-30
You need to attempt an install of the deb files first. What files are they?

---

### Post by hakermania on 2011-08-30
Hello aronin, the most possible thing is that the deb files will need more dependencies and that means internet connection if they are not installed.
Ubuntu is an internet-based distro and you'll have a hard time.

---

### Post by akoskm on 2011-08-30
> **aronin said:**
> I've installed ubuntu 11.04 .but i  don't have an internet connection. I have these deb files taken from my friends computer (from /var/cache/apt/archives).please help me to install this files without any dependency problem.

1. take the required .deb from your friend's computer
2. attempt to install the actual package
```

sudo dpkg -i /path/to/the/installer/somefile.deb

```
3. read the output, are there any dependencies missing:
yes) 1.
no) done.

---

### Post by akoskm on 2011-08-30
> **hakermania said:**
> ...
Ubuntu is an internet-based distro
...
[IMG]http://img710.imageshack.us/img710/7025/dudewtf.th.jpg[/IMG]

---

### Post by vijushimpi on 2011-08-30
On the new Computer
```
cd thedebfolder
dpkg -i *
```

this is work all the time but, in the old cache if you installed ubuntu updates chances are that it can give problems.

---

