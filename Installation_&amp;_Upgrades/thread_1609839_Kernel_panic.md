---
title: "Kernel panic"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by wp95 on 2010-10-30
Hi. I have upgraded from 10.4 to 10.10, and when I restart I get the error "kernel panic - not syncing: VFS: unable to mount root fs on unknown block".
I've done some googling and found this is a pretty common problem, but no existing solutions have worked for me. Also I'm sorry but I'm not sure what other information would be needed to help fix this. Right now I am using the 10.4 live CD. Thanks for any help.

---

### Post by mörgæs on 2010-10-31
In my experience it is not worth trying to fix a kernel panic. This might help:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by wp95 on 2010-11-07
If it's not worth trying to fix it, do you think I simply can't use Ubuntu? I've spent the entire week now doing a complete reinstall. The new install worked for about 5 restarts before it started giving the same error message as well. I had all updates disabled so I know it wasn't something new that was installed. Then I tried another new install on a new hard disk, and the same thing - it works a few times, then seemingly randomly gives this message again. Is anyone else experiencing the same thing?

---

### Post by dino99 on 2010-11-07
many users, like myself, have this issue, mostly due to bad kernel compilation or driver(s) you need not compiled into this kernel. Actually i use 2.6.37 from natty, with the best result, but still give me a "unknown block" on the first boot, then its ok.

wonder if its due to kernel or gparted issue, might be a good idea to reformat with the latest partedmagic before reinstalling again.

---

### Post by wp95 on 2010-11-07
ok, sounds like a good place to start, I'll post the result.

---

### Post by wp95 on 2010-11-13
So after another week of stuffing around with it I was able to solve all my problems. I went out and bought a copy of Windows 7. Works perfectly.

---

