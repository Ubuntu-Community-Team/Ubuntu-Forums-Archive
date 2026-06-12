---
title: "cannot boot ubuntu after changing delay time to 0 in menu.lst"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by kanna1620 on 2007-06-23
HI friends!
               This is Kanna. Ubuntu 7.04 user. For some reason I have to make the default option in /boot/menu.lst to load windows. And I gave the delay time as 0 sec. Now my problem is Ubuntu is not loading at all. I dont want to work in windows. But I dont know how to load Ubuntu as it is not displaying any menu to choose the operating system. It is only loading windows. I dont know how to rectify this error. Somebody please help me. Thanks in advance.
With regards
                  kanna.

---

### Post by confused57 on 2007-06-23
You'll need to mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then you change the timeout to something like 3 seconds.

---

