---
title: "Clean Up /boot 16.4.1"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by richramik on 2016-07-30
I just upgraded to 16.04.1.  WOuld like to know if the following still applies to cleaning up /boot.

START CLEAN UP
     sudo apt-get autoremove

CLEAN /BOOT (without the double quotes at the beginning and end)
     "dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge"


Thanks,
Rich Ramik

---

### Post by deadflowr on 2016-07-30
Sure, that'll work.
But an even easier thing is to install byobu
```
sudo apt install byobu
```
then you can run the purge-old-kernels command
```
sudo purge-old-kernels
```
which by default keeps two kernels, instead of only one, like the dpkg command does.
But it can remove all (except the running kernel, of course) or even keep ten kernels if you want, as it has a parameter (and a man page) for that.

---

### Post by DuckHook on 2016-07-31
In Xenial, I believe it is no longer necessary to install byobu or any package to purge old kernels (though byobu is a great app for many other reasons and its kernel purging script is a handy extra tool). However, one needs to use the new *apt* command instead of *apt-get* as follows:```
sudo apt autoremove --purge
```…this will keep just the two latest kernels and purge the rest.

---

### Post by richramik on 2016-07-31
Hey, thanks for the info.

Rich Ramik

---

