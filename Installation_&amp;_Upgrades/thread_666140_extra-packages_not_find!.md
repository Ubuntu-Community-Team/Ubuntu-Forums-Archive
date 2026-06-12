---
title: "extra-packages not find!"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by dukedome on 2008-01-13
when i try to execute in terminal the comand:

sudo apt-get install ubuntu-restricted-extras

says that impossible to find!
So, wwwwwwwhat can i do? Help me please!

---

### Post by kostkon on 2008-01-13
It seems you don't have the necessary repository enabled.

Go to *System -> Administration -> Software Sources*, and in the first tab select any repositories that are not already selected (actually for *ubuntu-restricted-extras* you need the *multiverse* reporitory), i.e. *universe*, *main*, *multiverse*, *restricted*. Press *Close* and then try again to install the package you want.

---

### Post by dukedome on 2008-01-13
Hey, it works! Thankyou Man!

---

