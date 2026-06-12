---
title: "Can't Enable Compiz"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by GuitarRocker2562 on 2008-09-08
I just installed Intrepid Alpha 5 (I had Intrepid update before, but I just wanted to reinstall). Anyway, now I can't enable compiz, I have tried going to appearance and enabling it there, and after a few minutes it said it cannot enable compiz. So, quite naturally I fired up bash and entered ```
compiz --replace
``` and it didn't work. The terminal output is: ```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity 

```

So obviously it didn't work. I am using an Intel 915GV Express graphics card.

Any ideas?

---

### Post by GuitarRocker2562 on 2008-09-08
nobody?

---

### Post by blackphiber on 2008-09-08
same.

using an ati radeon 9200 with the OSS driver.

too busy right now to report a bug, but if you do, let us know.

---

### Post by RAOF on 2008-09-09
It would be useful if you could post your /etc/X11/xorg.conf and /var/log/Xorg.0.log files.  It looks like glxinfo is segfaulting, which either indicates that your 3d stack is seriously messed up, or, more likely, that you're using the VESA driver :).

---

### Post by cdtech on 2008-09-09
You could try the program "compiz-check" here:
[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check)
Lot of information.

---

### Post by blackphiber on 2008-09-09
[https://bugs.launchpad.net/ubuntu/+bug/268006](https://bugs.launchpad.net/ubuntu/+bug/268006)

---

### Post by RAOF on 2008-09-09
> **RAOF said:**
> It would be useful if you could post your /etc/X11/xorg.conf and /var/log/Xorg.0.log files.  It looks like glxinfo is segfaulting, which either indicates that your 3d stack is seriously messed up, or, more likely, that you're using the VESA driver :).

In light of the above bug, I amend this to include: *or have installed the nvidia binary driver*.  I'm not entirely sure why people do this, but it breaks your 3d!

EDIT: It seems that this was fallout of a packaging bug, where nvidia-glx-173 was accidentally pulled in in some cases where it's not needed.

---

