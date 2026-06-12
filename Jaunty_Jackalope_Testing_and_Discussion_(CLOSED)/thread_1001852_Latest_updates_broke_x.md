---
title: "Latest updates broke x"
date: 2008-12-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mgiacchetti on 2008-12-04
Anyone know why the latest updates broke x??

At boot, i received the CLI and i had to 

```

startx

```to get the gui working.

logout broken as well.


ok, so I restarted, unplugged my external drive, and it worked fine..
after second restart (the one mentioned above) logout is not broken anymore.

---

### Post by shirishagarwal on 2008-12-04
Mgiacchetti if you have intel hardware you may have been hit with [http://ubuntuforums.org/showthread.php?t=998754](http://ubuntuforums.org/showthread.php?t=998754) .

You can find what your graphics card is by going into recovery into root and doing 

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```

This will give you info. about your chipset. As can be seen mine is an ancient Intel 845G/GL chipset.

---

