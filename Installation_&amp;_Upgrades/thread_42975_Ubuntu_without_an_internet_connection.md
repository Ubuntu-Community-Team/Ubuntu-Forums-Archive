---
title: "Ubuntu without an internet connection"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by leji on 2005-06-20
Hi,

my neighboor doesnt have internet access, is there a way to download packages from my computer, burn them on a CD and install them on his computer ?
He runs ubuntu, I run gentoo so I cant get them through apt

I hope you understood the question :D

Thanks

---

### Post by tristan on 2005-06-20
I do it all the time - download large ubuntu deb packages where I have access to a high speed connection, put them on a flashdrive and install them on my (slow dialup) ubuntu box at home using **sudo dpkg -i name_of_the.deb**.

You can google "ubuntu name_of_package" and it'll usually return something like **Ubuntu -- name_of_package**.

Or better, find a decent ubuntu mirror.

---

### Post by xristos on 2005-06-20
You can search for packages here ---> [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And then install them using 

```
dpkg -i package.deb
```

---

### Post by leji on 2005-06-20
Ok, thank you, just another question :
Do i have to do dpkg -i package.deb for each package or can it grab the packages needed for dependancies automatically from a local path ?

---

