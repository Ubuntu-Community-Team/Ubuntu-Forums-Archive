---
title: "Hope for Jaunty -- Fix qt4"
date: 2008-12-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by keeler1 on 2008-12-10
It would be great if qt4 could be done right in Jaunty.  Especially phonon.  Currently it is broken in intrepid.  The phonon backends and development files are all put into the incorrect directories. 

All qt libraries should be independent of kde.  This is my hope for Jaunty.

---

### Post by RAOF on 2008-12-10
> **keeler1 said:**
> It would be great if qt4 could be done right in Jaunty.  Especially phonon.  Currently it is broken in intrepid.  The phonon backends and development files are all put into the incorrect directories. 

All qt libraries should be independent of kde.  This is my hope for Jaunty.

There's a bug report on launchpad, right?  Otherwise this hope will remain a hope.

---

### Post by keeler1 on 2008-12-10
Yes there is a bug report.  I am not very familiar with how things are packaged but it seems like it would be fairly easy to fix.

QMake does not point to the correct phonon library location.  Therefore all the makefiles it generates do not compile without tinkering with the makefiles myself.

---

