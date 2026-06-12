---
title: "Ubuntu 10.4 can not controll Brightness"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by luckysanj on 2011-05-04
Hello Dear All,

[FONT=Times New Roman][SIZE=2]**Brightness Problem ****Dell Inspiron 14R N4010 Problems **[/SIZE][/FONT]             
                                                                [FONT=Times New Roman][SIZE=2]Hey Guys,
I freshly installed Ubuntu 11.4 on my laptop Del Inspirion 14 N4010 but in my laptop there is Brightness controll problem. I read all of forum posted matter for brightness but it didnt work.

Brightness up down keys moves the brightness slider around but doesn't change the actual brightness. I am also not able to change the brightness using the power management tool also.
This problem is draining my battery life crazy.[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=2]System Information[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Model: INSPIRON N4010[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Service Tag:97P3ZL1[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Express Service Code: 200-564-807-41[/SIZE][/FONT]
[SIZE=2][FONT=Times New Roman]CPU: i3 processor [/FONT][/SIZE]


[SIZE=2]Help will be appreciated Thank You.[/SIZE]


Regards,
Luckysanj

---

### Post by lechien73 on 2011-05-04
Hi,

It appears to be a kernel bug, which is open in Launchpad (#568611).

A PPA has been created, which contains a workaround - although be warned that this installs a new kernel, which may conflict with future kernel updates from the official repositories.

The link and installation instrucitons are here: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

---

