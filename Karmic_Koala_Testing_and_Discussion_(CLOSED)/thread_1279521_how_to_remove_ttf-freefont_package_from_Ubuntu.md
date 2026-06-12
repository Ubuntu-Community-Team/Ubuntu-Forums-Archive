---
title: "how to remove ttf-freefont package from Ubuntu?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ani on 2009-09-30
I am trying to remove ttf-freefont package to replace it with better fonts, however when I try to remove it, it wants to remove most of my system packages? Why? Is there a way to get around this?

---

### Post by autocrosser on 2009-09-30
Why don't you just make a .fonts in your /home & put all the extra fonts you want there? I have about 500 fonts installed on my system--almost all in my /.font folder.

---

### Post by Ani on 2009-09-30
I am also putting my fonts into .fonts folder.

but I also want to be able to remove ttf-freefont

---

### Post by autocrosser on 2009-10-01
HMMMM---looks like the linux printing packages use it, so unless you don't need printing--it's a non-happening...

---

### Post by dinxter on 2009-10-01
only the cups printing system depends on it here as autocrosser says, is it not better to just keep the package and install the additional 'better' fonts you want and set the desktop or whatever applications to use them instead? i.e.  ttf-freefont fonts can be replaced without actually removing the package that makes these fonts available

---

### Post by Ani on 2009-10-01
on Ubuntu 9.10 beta it is not only cups system, but ALL pacakges depend on ttf-freefont.

---

