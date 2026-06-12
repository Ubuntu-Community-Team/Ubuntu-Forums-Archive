---
title: "Can't Install Eclipse"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by raronson on 2009-08-23
Hi.  Since upgrading from 9.04 I haven't been able to install Eclipse.  I initially just did a dist-upgrade, and thought that the problem might be due to mixed repository data, but after a reformat and clean install of Karmic Alpha 4, I still get the following message when trying to install Eclipse (after daily updates for the last week or so):

```

eclipse:
 Depends: eclipse-jdt but it is not going to be installed
 Depends: eclipse-pde but it is not going to be installed
 Depends: eclipse-source but it is not going to be installed
 Recommends: eclipse-gcj but it is not going to be installed

```

It's not such a big deal that I can't use it at the moment, but I'd just like to know what's going on.  Thanks for any help or a point in the right direction.

---

### Post by chrisccoulson on 2009-08-23
Seems to be [https://bugs.edge.launchpad.net/ubuntu/+source/eclipse/+bug/401402]("https://bugs.edge.launchpad.net/ubuntu/+source/eclipse/+bug/401402")

---

### Post by raronson on 2009-08-23
Baaaahh, I feel sheepish.

Thanks a ton.

EDIT: nevermind.  The workaround removes tuxguitar, which I use.

---

### Post by ktp on 2009-08-23
you can always download the zip file and just unzip it...I do that since package is not updated.

---

### Post by raronson on 2009-08-23
Works perfectly, thanks.

---

