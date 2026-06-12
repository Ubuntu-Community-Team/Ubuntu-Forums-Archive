---
title: "No space in boot partition"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by alawson on 2012-09-29
Hi all,

I have a problem with my Ubuntu server. It's not a big deal, I could blow the OS away - this is really just a play box.

When I try and run apt-get upgrade I get errors which indicate that the boot partition is full - which it is;

```
df -kh
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/headless-root   913G  193G  675G  23% /
udev                        3.9G  8.0K  3.9G   1% /dev
tmpfs                       1.6G  560K  1.6G   1% /run
none                        5.0M     0  5.0M   0% /run/lock
none                        3.9G     0  3.9G   0% /run/shm
cgroup                      3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1                   228M  221M     0 100% /boot
```


How do I clear some space?
Running apt-get autoremove gives an error indicating that /boot is full and it can't complete. If I move one of the bigger files to another partition I get errors indicating a broken dependency. This seems like a circular problem - not enough room to clear some room. Any other options apart from blowing away the OS and filing this under things to watch out for?

---

### Post by jerrrys on 2012-09-29
You need to remove some of those old kernels.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=boot+partition+full&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=boot+partition+full&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by alawson on 2012-09-29
Thanks jerrrys - using your link I found the following page;

[http://www.upubuntu.com/2011/11/how-to-remove-unused-old-kernels-on.html]("http://www.upubuntu.com/2011/11/how-to-remove-unused-old-kernels-on.html")

I used the sudo aptitude purge command to remove kernels one at a time, which did the trick;

```
df -kh
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/headless-root   913G  191G  676G  23% /
udev                        3.9G   12K  3.9G   1% /dev
tmpfs                       1.6G  560K  1.6G   1% /run
none                        5.0M     0  5.0M   0% /run/lock
none                        3.9G     0  3.9G   0% /run/shm
cgroup                      3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1                   228M   27M  189M  13% /boot
```

---

### Post by jerrrys on 2012-09-29
.. :)

---

