---
title: "After upgrading to Natty, can't mount DVD"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by Nutria on 2011-10-07
This worked perfectly under 10.10 Meerkat.  Yes, I'm in the plugdev group.

Any thoughts?

(I must say that I'm **very** disappointed in Natty, since I'm also having problems with window jerkiness, OpenGL weirdness and the inability to access Workspaces other than #1.  One would think that after 6 months, such bugs would be fixed.)

---

### Post by raja.genupula on 2011-10-08
[http://ubuntuforums.org/showthread.php?t=1549545](http://ubuntuforums.org/showthread.php?t=1549545)

try this

---

### Post by Nutria on 2011-10-08
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=1549545](http://ubuntuforums.org/showthread.php?t=1549545)

try this

You're missing the points that 
(a) it worked in 10.10, and
(b) it's a permissions problem.

---

### Post by raja.genupula on 2011-10-08
please try it man.

---

### Post by Pumalite on 2011-10-08
If its attached to a SATA 3 Port; it will not work.

---

### Post by Nutria on 2011-10-08
> **Pumalite said:**
> If its attached to a SATA 3 Port; it will not work.

Since it worked in Maverick 10.10, for it not to work in Natty would be a serious regression not to be fixed in 6 months,

---

### Post by Nutria on 2011-10-08
> **raja.genupula said:**
> please try it man.

OK, I tried it, and it mounts.  But that's not the point of automount, is it?

```
$ sudo mount -v /dev/sr0 /media/DVD
mount: you didn't specify a filesystem type for /dev/sr0
       I will try type udf
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you didn't specify a filesystem type for /dev/sr0
       I will try type udf
/dev/sr0 on /media/DVD type udf (ro)
```

---

### Post by raja.genupula on 2011-10-08
[http://ubuntuforums.org/showthread.php?t=28555](http://ubuntuforums.org/showthread.php?t=28555)
hi
i am trying to help you
follow that.all steps.
let me know what you got.


all the best

---

### Post by Nutria on 2011-10-08
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=28555](http://ubuntuforums.org/showthread.php?t=28555)
hi
i am trying to help you
follow that.all steps.
let me know what you got.

Did you not see that I manually mounted the disk?  That has nothing to do with the file corruption problem in 28555.

---

### Post by Nutria on 2011-10-09
Solved by upgrading back to Maverick 10.10.  Received the "side" benefit of smoothly moving windows.

---

