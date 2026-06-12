---
title: "Sources.list file"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by nolandpete on 2007-08-18
Hi
I am sort of new with Ubuntu. I have just installed it and want to install libdvdcss2 package. but the sources.list file was created under root. when I edit the file I can not save it. When I installed UBUNTU I used my name as user name. So how can I edit the sources.list.

Thanks

---

### Post by merlinus on 2007-08-18
```

gksudo gedit /etc/apt/sources.list

```

-merlin

---

### Post by nolandpete on 2007-08-19
Hi Merlin

Why can I not use just any editor and can you explain the command. I have an other problem aside from the fact that I am French speaking. I downloaded a compresses archive XE122.tgz. It is a mainframe style editor. I extracted  it on the desktop and then just creaated a shortcut to the executable.  I tried to use it to edit SOURCES.list but could not save the file.

Thanks for your help

---

### Post by merlinus on 2007-08-19
gksudo preceding a terminal command runs a graphical application as root.

sudo will run a non-graphical app as root.

You can use any editor you like (gedit is a graphical one), and this will allow you to edit and save files such as /etc/apt/sources.list.

-merlin

---

### Post by Pumalite on 2007-08-19
Want to edit sources.list?. Just do what Merlin recommended.

---

