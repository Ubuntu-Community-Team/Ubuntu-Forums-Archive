---
title: "ls in grub not equal  df in shell&#65311;"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by luofeiyu on 2012-06-11
in my  shell:
root@debian:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             28836860   3309556  24062472  13% /
tmpfs                   512948         0    512948   0% /lib/init/rw
udev                    508508       216    508292   1% /dev
tmpfs                   512948         0    512948   0% /dev/shm
/dev/sda5              9611492    166816   8956436   2% /boot
/dev/sda6             45653024   8063188  35270784  19% /home

in my grub,
grub>ls
(hd0&#65292;msdos7),(hd0&#65292;msdos6),(hd0&#65292;msdos3),(hd0&#65292;msdos2),(hd0&#65292;msdos1)


#(hd0&#65292;msdos2),(hd0&#65292;msdos1)  are  windows  partition
i find  two strange thing:
1.
(hd0&#65292;msdos7)=/dev/sd6
(hd0&#65292;msdos6)=/dev/sd5
(hd0&#65292;msdos3)=/dev/sd3

2.when in grub,input
grub> ls (hd0,msdos1)/
it is ok, many files are listed

grub>ls (hd0,msdos2)/
the computer will be reopened,nothing listed .
in fact ,there are many files too in the  (hd0,msdos2) such as  (hd0,msdos1)
why i get nothing?
why pc reopened automatically?when i input ls (hd0,msdos2)/  ?

is there a virus  in my prtition2&#65311;

---

### Post by braaal on 2012-06-20
I think partition (2) is  Extended partition

this is normal ..

^_^

---

