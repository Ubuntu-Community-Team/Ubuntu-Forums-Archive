---
title: "Synaptic Package Manager is stuck when upgrading"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by Diablo713 on 2008-09-28
When ever i try to upgrade Synaptic package it gets stuck on package 71 out of 73. has to do with some freecontrib website or something.
here is a screenshot.
[IMG]http://file:///home/diablo/Desktop/Screenshot-Downloading%20package%20information-1.png[/IMG]
[IMG]http://file:///home/diablo/Desktop/Screenshot-synaptic.png[/IMG]

---

### Post by Elfy on 2008-09-28
The screenshot is conspicuous by it's absence.

Run ```
sudo apt-get update
``` and post the output please.

---

### Post by Diablo713 on 2008-09-28
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Diablo713 on 2008-09-28
Sorry about the screenshots on the first post,but i uploaded them.

---

### Post by cariboo on 2008-09-28
Why not try a different mirror. Go to System-->Administration-->Software Sources and change the download server there.

Jim

---

### Post by Elfy on 2008-09-29
What version of ubuntu are you using, it looks like it's hanging on dapper repos. Can you post your sources list please

```
cat /etc/apt/sources.list
```

---

### Post by Diablo713 on 2008-09-29
as for changing the mirror i am sorry to tell you it didnt work,its still stuk at the same place.:(

---

### Post by Diablo713 on 2008-09-29
Here is what happened when i cat /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

---

### Post by Elfy on 2008-09-29
It would appear that there is something amiss with the plf repos, you can comment them out for the moment if you want

```
sudo nano -B /etc/apt/sources.list
```

Go to the 2 freecontrib lines at the bottom and put # at the beginning of each
> [COLOR="#ff0000"]#[/COLOR]deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
[COLOR="Red"]#[/COLOR]deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

save and close - Ctrl+X, y and enter

Run an update

```
sudo apt-get update
```

---

### Post by Diablo713 on 2008-09-29
Thanks it worked.

---

### Post by Diablo713 on 2008-09-30
Btw is overlooking those paclages a bad thing to do,was i supposed to install them.

---

