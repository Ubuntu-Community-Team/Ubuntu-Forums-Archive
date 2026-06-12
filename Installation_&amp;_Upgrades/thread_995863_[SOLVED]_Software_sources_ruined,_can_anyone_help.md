---
title: "[SOLVED] Software sources ruined, can anyone help?"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by longlivethebestos on 2008-11-28
Hi there I just installed Linux mint, Then I wanted open office 3, so I thought I would be clever and use the repository from Ubuntu, and that didn't go down well. Why? because I tried to add it through terminal and heres what I typed;

**sudo wget [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main.list -O /etc/apt/sources.list.d/oo3.list**

Everything looked fine until I went into the software manager

and here's the error message: 

[[IMG]http://img509.imageshack.us/img509/6381/85692446xx7.png[/IMG]](http://img509.imageshack.us/my.php?image=85692446xx7.png)

I was thinking there was a way to delete what i had created?

Help would be appreciated

Thanks

---

### Post by taurus on 2008-11-28
Well, you can just delete /etc/apt/sources.list.d/oo3.list.

```
sudo rm /etc/apt/sources.list.d/oo3.list
```

---

### Post by longlivethebestos on 2008-11-28
Thank you sooooooooooooooooooooooooooooooooooo much.


OMG 



Thank you!

---

