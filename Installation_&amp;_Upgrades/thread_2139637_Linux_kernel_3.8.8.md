---
title: "Linux kernel 3.8.8"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by OMAR FARUK on 2013-04-27
Please some one tell me how can I install linux kernel 3.8.8 in my ubuntu 12.10

---

### Post by fragtion on 2013-04-27
Better off updating to 13.04 imho, that way all (updated) packages are certified compatible with 3.8

---

### Post by pqwoerituytrueiwoq on 2013-04-27
I have used the 3.8 kernel and the 3.9 kernel on 12.10 without issue

the easy way:
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

3.8.9 is out BTW

use this command in place of the last one
for the latest 3.8
```
KernelUpdateChecker -v 3.8 -r raring
```
for 3.8.8
```
KernelUpdateChecker -v 3.8.8 -r raring
```
for the latest 3.9 kernel (currently rc8)
```
KernelUpdateChecker -r raring
```

---

### Post by OMAR FARUK on 2013-04-27
[B][COLOR=#000000]to [fragtion]("http://ubuntuforums.org/member.php?u=625477"): isn't ubuntu 13.04 an unstable version?
[/COLOR][/B]

---

### Post by pqwoerituytrueiwoq on 2013-04-27
13.04 went 'stable' last Thursday

---

### Post by cvnmjs on 2013-05-03
[SIZE=3][FONT=system]This came in handy. Thanks![/FONT][/SIZE]:D

---

