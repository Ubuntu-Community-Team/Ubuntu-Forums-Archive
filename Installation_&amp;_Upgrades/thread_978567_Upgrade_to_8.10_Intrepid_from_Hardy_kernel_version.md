---
title: "Upgrade to 8.10 Intrepid from Hardy kernel version mismatch"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by picpic on 2008-11-11
Hi!

I just upgraded from Hardy to Intrepid. Can someone explain me why my kernel is still 2.6.24-19-generic ?

# uname -r
2.6.24-19-generic

I need to reinstall the Nvidia drivers, and as you may know, they require the kernel source. So I installed them:

# apt-get source linux-image-$(uname -r)

But another version got installed (2.6.27-7-generic):

# ls -lrt /usr/src
total 12
drwxr-xr-x 22 root root 4096 2008-11-10 13:41 linux-headers-2.6.27-7
drwxr-xr-x  7 root root 4096 2008-11-10 13:41 linux-headers-2.6.27-7-generic

The Nvidia installation script gets confused and fails reporting it cannot find the kernel source.

I'm confused too: what should my kernel version be after upgrading for Hardy to Intrepid, 2.6.27-7-generic or 2.6.24-19-generic ?

---

### Post by bijanafx on 2008-11-13
I am having this problem as well on my Dell Inspiron. Quite confusing. And I need to boot the latest kernel to load virtual box! If you find anything out, please let me know.

---

### Post by XFocus on 2008-11-22
Having the same issue.  Does anyone know what needs to be done?

---

### Post by XFocus on 2008-11-24
Bump

---

### Post by XFocus on 2008-11-24
Found the solution!

For anyone interested:
[http://ubuntuforums.org/showpost.php?p=6169997&postcount=12](http://ubuntuforums.org/showpost.php?p=6169997&postcount=12)

---

