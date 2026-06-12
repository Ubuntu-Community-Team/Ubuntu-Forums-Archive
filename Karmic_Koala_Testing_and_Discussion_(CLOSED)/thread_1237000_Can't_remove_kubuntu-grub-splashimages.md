---
title: "Can't remove kubuntu-grub-splashimages"
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by malachi1990 on 2009-08-10
I recently installed the package, thinking I could use it to theme grub2, but didn't realize that it depends on grub. It installed just fine, but now it can't update, nor can I remove it. This is the output:

Removing kubuntu-grub-splashimages ...
sed: can't read /boot/grub/menu.lst: No such file or directory
Your old /boot/grub/menu.lst file will be saved as /boot/grub/menu.lst.090810222537
mv: cannot stat `/boot/grub/menu.lst': No such file or directory
dpkg: error processing kubuntu-grub-splashimages (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 kubuntu-grub-splashimages
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
Any help would be appreciated.

---

### Post by wayne_cat on 2009-08-10
just tested on my system ... create a menu.lst file
```

sudo touch /boot/grub/menu.lst
```then it works

```
root@macbook:~# apt-get remove kubuntu-grub-splashimages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kubuntu-grub-splashimages
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 340kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 233724 files and directories currently installed.)
Removing kubuntu-grub-splashimages ...
sed: can't read /boot/grub/menu.lst: No such file or directory
Your old /boot/grub/menu.lst file will be saved as /boot/grub/menu.lst.090811043251
mv: cannot stat `/boot/grub/menu.lst': No such file or directory
dpkg: error processing kubuntu-grub-splashimages (--remove):
 subprocess installed pre-removal script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)


root@macbook:~# touch /boot/grub/menu.lst


root@macbook:~# apt-get remove kubuntu-grub-splashimages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kubuntu-grub-splashimages
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 340kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 233724 files and directories currently installed.)
Removing kubuntu-grub-splashimages ...
Your old /boot/grub/menu.lst file will be saved as /boot/grub/menu.lst.090811043314
dpkg: warning: while removing kubuntu-grub-splashimages, directory '/boot/grub' not empty so not removed.
root@macbook:~# 


```delete the menu.lst* files ... done

---

### Post by malachi1990 on 2009-08-10
Thanks!

---

