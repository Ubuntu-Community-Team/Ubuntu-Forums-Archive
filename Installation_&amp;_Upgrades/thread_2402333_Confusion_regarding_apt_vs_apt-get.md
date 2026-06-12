---
title: "Confusion regarding apt vs apt-get"
date: 2018-09-28
forum: Installation &amp; Upgrades
---

### Post by jimbolaya on 2018-09-28
I did a brief search to see if I could find the answer myself, but I'm afraid the terms are so common, I couldn't parse the search results for this forum. Other articles online indicate that there shouldn't be any difference between running ```
apt-get upgrade
``` and ```
apt upgrade
```

I was checking to see if my 16.04 install needed any upgrades. So I ran:

```
# apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386 libjpeg-progs libjpeg-turbo-progs libwayland-egl1-mesa linux-generic
  linux-generic-hwe-16.04 linux-headers-generic linux-headers-generic-hwe-16.04 linux-image-generic linux-image-generic-hwe-16.04
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

```

Using apt:

```
# apt upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libllvm5.0 libllvm5.0:i386
Use 'apt autoremove' to remove them.
The following NEW packages will be installed:
  amd64-microcode intel-microcode iucode-tool libllvm6.0 libllvm6.0:i386 linux-headers-4.15.0-34 linux-headers-4.15.0-34-generic
  linux-headers-4.4.0-135 linux-headers-4.4.0-135-generic linux-image-4.15.0-34-generic linux-image-4.4.0-135-generic
  linux-image-extra-4.4.0-135-generic linux-modules-4.15.0-34-generic linux-modules-extra-4.15.0-34-generic
The following packages have been kept back:
  libjpeg-progs libjpeg-turbo-progs
The following packages will be upgraded:
  libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386 libwayland-egl1-mesa linux-generic linux-generic-hwe-16.04
  linux-headers-generic linux-headers-generic-hwe-16.04 linux-image-generic linux-image-generic-hwe-16.04
11 upgraded, 14 newly installed, 0 to remove and 2 not upgraded.
Need to get 179 MB of archives.
After this operation, 786 MB of additional disk space will be used.

```

Why the enormous difference?

---

### Post by howefield on 2018-09-28
Try running 

```
sudo apt-get upgrade --with-new-pkgs
```

That should be the same as running sudo apt upgrade.

---

### Post by Bashing-om on 2018-09-28
jimbolaya; Hi :)

A bit of explaining and background:
[https://www.reddit.com/r/linux/comments/26q2sm/apt_vs_aptget/](https://www.reddit.com/r/linux/comments/26q2sm/apt_vs_aptget/)
[http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)
[https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)

[INDENT][INDENT]hope these help
[/INDENT][/INDENT]

---

### Post by hrsetrdr on 2018-09-29
From the[ howtogeek ]("http://www.howtogeek.com/234583/simp...ad-of-apt-get/")article:

```
sudo apt install package
```

Nice!   I was not aware.        

[IMG]https://i.imgur.com/ePwzQEc.png[/IMG]

---

