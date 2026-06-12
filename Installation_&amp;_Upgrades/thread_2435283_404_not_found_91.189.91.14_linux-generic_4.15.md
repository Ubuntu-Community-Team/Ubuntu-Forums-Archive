---
title: "404 not found 91.189.91.14 linux-generic 4.15"
date: 2020-01-18
forum: Installation &amp; Upgrades
---

### Post by sousedstvi2 on 2020-01-18
trying to make space for some updates, i accidentally deleted some linux files. oops.

when I run

sudo apt --fix-broken install

I see

Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main i386 linux-generic i386 4.15.0.52.54
  404  Not Found [IP: 91.189.91.14 80]
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main i386 linux-image-generic i386 4.15.0.52.54
  404  Not Found [IP: 91.189.91.14 80]
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main i386 linux-headers-generic i386 4.15.0.52.54
  404  Not Found [IP: 91.189.91.14 80]

---

### Post by deadflowr on 2020-01-18
That particular version doesn't seem to exist anymore, it was updated to 4.15.0-52.56
Is there something wrong with
```
sudo apt update
```
post back the results.

---

### Post by sousedstvi2 on 2020-01-18
thanks for the reply!

christopher@fern:~$ sudo apt update
.
a  bunch of HIT . . . . .lines
.
Fetched 6,599 kB in 4s (1,527 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
603 packages can be upgraded. Run 'apt list --upgradable' to see them.

603 packages is a lot. so
$apt list --upgradable | grep linux-headers
linux-headers-generic/bionic-updates,bionic-security 4.15.0.74.76 i386 [upgradable from: 4.15.0.46.48]

so I went ahead and tried again.
christopher@fern:~$ sudo apt --fix-broken install

this time I got no error fixing those missing deps.

why is that? is it because apt update tells --fix-broken to get the most up-to-date version of those image and header files?

---

### Post by deadflowr on 2020-01-18
sudo apt update refreshes the package list on your machine by grabbing the latest listings from the archives.
Always run it before running any other apt commands.

So, what did you actually delete...

---

