---
title: "calculator not launching"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by kernelnewbie1 on 2010-03-16
Well every thing was fine before i tried to tweak the gcalctool ,
i made some changes , built it successfully and also installed it

but now when i launch it says

"The user interface file /usr/local/share/gcalctool/gcalctool.ui is missing or unable to be loaded. Please check your installation"

but i have /usr/local/share/gcalctool/gcalctool.ui !!

Please help me .

--- ubuntu is gr8

---

### Post by khelben1979 on 2010-03-16
Were you able to launch it and then it stopped working? :-/

---

### Post by wojox on 2010-03-16
```
sudo apt-get install gcalctool
```

That should fix it. ;)

---

### Post by kernelnewbie1 on 2010-03-16
> **khelben1979 said:**
> Were you able to launch it and then it stopped working? :-/

Calculator was working fine before built new source code and installed it , after installing new gcalctool , every time i do Application->accessories->Calculator i get error message

> **wojox said:**
> ```
sudo apt-get install gcalctool
```That should fix it. ;)

i tried this twice , but its not working

---

### Post by kernelnewbie1 on 2010-03-19
fixed ;) !

first i un-installed the new version which i had built and installed , then installed gcalctool from apt-get !
there was a bug in new verision which i compiled and hence was the problem,

i dont understand why new installation overwrites old , or atleast prompt to remove old

---

