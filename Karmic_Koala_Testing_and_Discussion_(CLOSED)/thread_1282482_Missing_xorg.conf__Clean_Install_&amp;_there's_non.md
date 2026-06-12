---
title: "Missing xorg.conf???  Clean Install &amp; there's none!"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-04
No wonder why I can't get past the logo - I looked in /etc/ and there's no X11 directory, and thus no xorg.conf!

See this post for more info:

[http://ubuntuforums.org/showthread.php?p=8046744#post8046744](http://ubuntuforums.org/showthread.php?p=8046744#post8046744)

---

### Post by trulan on 2009-10-04
That's right, xorg.conf is nonexistent on a fresh install.  Everything is configured automatically.  If you run
```
sudo Xorg-configure
```
it will generate a basic xorg.conf that you can then edit.  However, you shouldn't need one to be able to boot the system, unless you require some special settings.

---

### Post by Zorael on 2009-10-04
There should still be an X11 directory, though.

Is (for instance) x11-common installed?

---

### Post by emarkay on 2009-10-04
> **Zorael said:**
> There should still be an X11 directory, though.
Is (for instance) x11-common installed?

I cd to /etc and then ls, and there is nothing displayed that says "X11" or "x11".  

Is there a possibility it's at the beginning of the list - how can you "pause" ls to only show one screen at a time; or say, 80 lines - it does appear to scroll off the screen and it's way to fast for me to hit the PAUSE key!

Thanks!

---

### Post by emarkay on 2009-10-04
> **trulan said:**
> That's right, xorg.conf is nonexistent on a fresh install.  Everything is configured automatically.  If you run
```
sudo Xorg-configure
```
it will generate a basic xorg.conf that you can then edit.  However, you shouldn't need one to be able to boot the system, unless you require some special settings.

I wanted to see if the xorg was the issue...
I am just trying (flailing, actually) to get a GUI...  See my post here:
[http://ubuntuforums.org/showthread.php?p=8046744#post8046744](http://ubuntuforums.org/showthread.php?p=8046744#post8046744)

Any ideas?

---

### Post by wojox on 2009-10-04
```
ls | less
```

Then hit your space bar to traverse the list. Q to escape.

---

