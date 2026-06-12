---
title: "Makin a .deb package"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by inashdeen on 2012-06-04
Hi everyone, let say i don't need to compile an apps. i have all the executable in their mock hierarchy like /usr, /usr/bin and /usr/share/applications, how do i compile them to .deb? a step by step procedure would be highly appreciated. thanks in advance.

---

### Post by Cheesemill on 2012-06-04
Have you read the Ubuntu packaging guide?

[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

### Post by oldos2er on 2012-06-04
If the packages will only be used on your own system, look into **checkinstall**: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by inashdeen on 2012-06-04
My issue is like this. Hope i am not being unclear. I already have the binary. I already have the hierarchy. I am not sure how to build the control. last time, I wrote them manually and package them in .deb, i result with bad packages error.

---

### Post by dino99 on 2012-06-04
might be of some help

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

