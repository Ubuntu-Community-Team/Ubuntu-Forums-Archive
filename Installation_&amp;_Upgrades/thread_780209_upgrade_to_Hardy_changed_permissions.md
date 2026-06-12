---
title: "upgrade to Hardy changed permissions"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by gkiteguy on 2008-05-03
I didn't know whether to post this in the newbee section. I upgraded from 7.2 and broke my monitor resolution. I tried to edit the xorg.conf and got a funny message in terminal. I can't modify or run any of the sudo stuff to fix it in terminal. My computer is identified as FAMUBUNTU

gordon@FAMUBUNTU:~$ sudo cp etc/X11/xorg.conf etc/X11/xorg.conf.bu
sudo: unable to resolve host FAMUBUNTU

Maybe I've forgotten something. Now what can I do?????:confused:

---

### Post by Standy on 2008-05-03
I've got the same problem.. might be something about user accounts and permissions? i havent upgraded or anything like that but.. i've messed around alot... cant start synaptic package manager either.. just says it's opening it and then closes it..for some strange reason.. driving me insane tho..

---

### Post by ansicplusplus on 2008-05-03
Hy,
your problem is that hardy can't find your hostname in /etc/hosts. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=770700]("http://ubuntuforums.org/showthread.php?t=770700")
Post #3 seems to be the easiest way to solve this.
Yours, ansicplusplus

---

### Post by gkiteguy on 2008-05-03
> **ansicplusplus said:**
> Hy,
your problem is that hardy can't find your hostname in /etc/hosts. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=770700]("http://ubuntuforums.org/showthread.php?t=770700")
Post #3 seems to be the easiest way to solve this.
Yours, ansicplusplus

Thanks very much, that did it. Looks like I need it, my printing is also tanked.:-k

---

