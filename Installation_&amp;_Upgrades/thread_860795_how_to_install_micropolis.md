---
title: "how to install micropolis"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Healer on 2008-07-15
how do i install micropolis, and don't tell to go to that monkeyblog crap cuz it's not working for it, i did it exactly how it told me and this is what it says:
jason@ubuntuCPxJ650:~$ cd /home/jason/Desktop/micropolis-activity
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ ./configure
bash: ./configure: No such file or directory
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ make
make: *** No targets specified and no makefile found.  Stop.
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$

---

### Post by iaculallad on 2008-07-15
> **Healer said:**
> how do i install micropolis, and don't tell to go to that monkeyblog crap cuz it's not working for it, i did it exactly how it told me and this is what it says:
jason@ubuntuCPxJ650:~$ cd /home/jason/Desktop/micropolis-activity
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ ./configure
bash: ./configure: No such file or directory
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ make
make: *** No targets specified and no makefile found.  Stop.
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$

Are you sure the ***configure*** file exist in your ~/Desktop/micropolis-activity directory?

```
ls
```

---

### Post by Healer on 2008-07-15
this is what pops up:
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ ls
activity  COPYING  __init__.py  Micropolis             Micropolis.png  res
cities    images   manual       micropolisactivity.py  README          src
i don't think so but i could be wrong

---

### Post by iaculallad on 2008-07-15
> **Healer said:**
> this is what pops up:
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ ls
activity  COPYING  __init__.py  Micropolis             Micropolis.png  res
cities    images   manual       micropolisactivity.py  README          src
i don't think so but i could be wrong

With this post from ls, I could say that the configure file does not exist on this directory. Try browsing the sub-directories if you could find the configure file and that's where you should issue your ./configure command.

---

### Post by oldos2er on 2008-07-16
> **Healer said:**
> this is what pops up:
jason@ubuntuCPxJ650:~/Desktop/micropolis-activity$ ls
activity  COPYING  __init__.py  Micropolis             Micropolis.png  res
cities    images   manual       micropolisactivity.py  README          src
i don't think so but i could be wrong

 Start by reading the README.

---

