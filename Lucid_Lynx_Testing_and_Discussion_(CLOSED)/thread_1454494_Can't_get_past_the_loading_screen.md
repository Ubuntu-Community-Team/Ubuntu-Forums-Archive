---
title: "Can't get past the loading screen"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dagur on 2010-04-14
I only see the ubuntu logo with the five dots below it. If I try to switch "views" with ctrl+alt+F1,2,3,etc  nothing happens. The computer only responds to ctrl+alt+delete.

What can I do to figure out what's going on?

:confused:

---

### Post by Ancanus on 2010-04-14
>  
What can I do to figure out what's going on? In GRUB, press CTRL+C over your ubuntu entry, remove the * quiet splash * lines and boot.

---

### Post by Dagur on 2010-04-15
Thanks. I did that and everything seemed to load without an error but no GUI appeared (I just saw the loading "checklist").
I tried logging in and write 'startx' and presto, my desktop was up and running without problems.

---

