---
title: "Segmentation fault (core dumped)"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rsvr85 on 2009-10-13
Hi all, I upgraded to Karmic x64 yesterday, Firefox was working fine, i boot up today and get this;
```
stu@ubuntu:~$ firefox
Segmentation fault (core dumped)
stu@ubuntu:~$ firefox --safe-mode
Segmentation fault (core dumped)

```

Any ideas?

---

### Post by LKjell on 2009-10-13
Install valgrind and use```
valgrind /usr/bin/firefox
``` And maybe something interesting will pop up.

---

### Post by taavikko on 2009-10-13
Propably it's settings have been corrupted.

Move the ~/.mozilla/ folder to safety and restart firefox.

---

### Post by rsvr85 on 2009-10-13
> **LKjell said:**
> Install valgrind and use```
valgrind /usr/bin/firefox
``` And maybe something interesting will pop up.

Here's the ouput of valgrind;

```
stu@ubuntu:~$ valgrind /usr/bin/firefox
==14599== Memcheck, a memory error detector
==14599== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==14599== Using Valgrind-3.5.0-Debian and LibVEX; rerun with -h for copyright info
==14599== Command: /usr/bin/firefox
==14599== 
Segmentation fault (core dumped)
stu@ubuntu:~$ valgrind /usr/bin/firefox-3.5
==14612== Memcheck, a memory error detector
==14612== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==14612== Using Valgrind-3.5.0-Debian and LibVEX; rerun with -h for copyright info
==14612== Command: /usr/bin/firefox-3.5
==14612== 
Segmentation fault (core dumped)

```

Moving the .mozilla folder didn't help either :(

---

### Post by rsvr85 on 2009-10-13
GlobalMenu was conflicting with Firefox, i uninstalled GlobalMenu from synaptic, reinstalled Firefox and all is now well.
Thanks for the suggestions guys :D

---

### Post by AlanRick on 2009-10-14
Hi RSVR85,
Thanks for the feedback. 
I have the same problem with firefox. How did you work out that it was another app causing the problem?

---

