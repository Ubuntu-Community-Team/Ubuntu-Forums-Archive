---
title: "update install trouble .. .run files?"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by CastorTroyXXIV on 2009-12-01
hi, what do i do with this file? this version of my graphics card is what im trying to get, i downloaded it from the website, its in linux. is that the right one? and how to i install it? it keeps giving me an error. do i install in terminal or something?

 NVIDIA-Linux-x86-96.43.14-pkg1.run

---

### Post by JBAlaska on 2009-12-01
Start a terminal and navigate to the directory where the install file is located, example: ```
# cd /home/yourusername/Downloads 
```

Then do:
```
# sudo sh NVIDIA-Linux-x86-96.43.05-pkg#.run
```

That should start the install program. let it modify your xorg.conf when asked and your done.

Please remember when you install a driver manually you will have to re-compile it when there is a kernel update, unless you register it with DKMS (google).

---

