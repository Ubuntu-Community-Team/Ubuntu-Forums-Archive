---
title: "Upgraded, now software doesn't work."
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by glennbates on 2014-09-07
I just upgraded to the latest version of Ubuntu. I use bluefish a lot. It still shows that it is installed but it is not working. I "unstalled" it ant then re"installed" it and it still isn't working. What could be wrong? How do I fix this problem?

---

### Post by Vladlenin5000 on 2014-09-07
What exactly isn't working?

---

### Post by glennbates on 2014-09-07
> **Vladlenin5000 said:**
> What exactly isn't working?

Nothing will. It will not even run. When I click the icon, it acts like it is going to open but then after about 15 to 20 seconds, it quits brightening and dimming and does nothing.

---

### Post by EuclideanCoffee on 2014-09-07
Did you purge the package and reinstall it?

sudo apt-get purge bluefish

---

### Post by Vladlenin5000 on 2014-09-07
Try running it in the terminal where some error messages will - hopefully - popup. Those errors may or may not give a clue about it.

(EDIT: After purging it following the previous advice and only IF that doesn't change the symptom).

---

### Post by glennbates on 2014-09-07
> **Vladlenin5000 said:**
> Try running it in the terminal where some error messages will - hopefully - popup. Those errors may or may not give a clue about it.

(EDIT: After purging it following the previous advice and only IF that doesn't change the symptom).

How?

---

### Post by glennbates on 2014-09-08
> **Vladlenin5000 said:**
> Try running it in the terminal where some error messages will - hopefully - popup. Those errors may or may not give a clue about it.

(EDIT: After purging it following the previous advice and only IF that doesn't change the symptom).

How do I run it from the terminal?

---

### Post by ian-weisser on 2014-09-09
Open a terminal

Type 'bluefish' and hit <ENTER>

Copy-and-paste any terminal output here.

Warning: If bluefish opens, it will be a child process of the terminal. Closing the terminal window will kill bluefish instantly without saving your work.

---

### Post by glennbates on 2014-09-09
> **ian-weisser said:**
> Open a terminal

Type 'bluefish' and hit <ENTER>

Copy-and-paste any terminal output here.

Warning: If bluefish opens, it will be a child process of the terminal. Closing the terminal window will kill bluefish instantly without saving your work.

This is what it says:

(bluefish:11058): GLib-ERROR **: /build/buildd/glib2.0-2.40.0/./glib/gmem.c:103: failed to allocate 18446744073683433938 bytes
Trace/breakpoint trap (core dumped)

---

### Post by glennbates on 2014-09-10
So, what do I do now?

---

### Post by glennbates on 2014-09-12
Any suggestions?

---

### Post by glennbates on 2014-09-14
Not sure what happened to my image on here.

---

