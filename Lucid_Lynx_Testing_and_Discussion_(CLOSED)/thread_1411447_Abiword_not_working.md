---
title: "Abiword not working?"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-02-19
I just noticed I can't open any of my abiword docs. I tried reinstalling abiword but still can't open any docs.

Just wondered if anyone else had noticed this.

Edit: just tried launching abiword from the menu and it's a no go.

Trying to launch from terminal produces this error:

> abiword: error while loading shared libraries: libgoffice-0.8.so.7: cannot open shared object file: No such file or directory


---

### Post by autocrosser on 2010-02-20
Yes---libgoffice-0.8.so.7 went MIA & you need to create a new link to so.8--then it works....do you want to do a bug report? I would guess that it will be updated fairly soon--would show up during a build......

---

### Post by kansasnoob on 2010-02-20
Update fixed it this AM :D

I'd actually noticed that day before yesterday, but this early in the development cycle I don't get too excited.

---

### Post by kansasnoob on 2010-02-20
testing 1-2-3 ................ wondering why this post didn't update?

---

