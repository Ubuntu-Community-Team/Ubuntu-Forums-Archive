---
title: "kubuntu down"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sena_akada on 2009-09-13
i edited my xorg.conf to get past the bsod caused by the latest updates, but it loads the hard-drive icon twice and the botts me back to the login screen. and it does this everytime i try to relogin :(

how do i remove the jockey nvidia driver with the console as i think this may be the problem

---

### Post by slakkie on 2009-09-13
dpkg -l | grep nvidea 

and select the packages you need to remove.. 

then 

aptitude purge package_name

---

