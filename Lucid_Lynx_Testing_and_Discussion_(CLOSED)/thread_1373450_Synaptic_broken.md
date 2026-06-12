---
title: "Synaptic broken"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-01-05
Hi

When I try to run synaptic I get prompted for my password as usual, then the synaptic window flashes up and then disappears.

This appears in syslog messages

Jan  5 23:37:13 USBKarmic kernel: [  977.962965] Process 2947(synaptic) has RLIMIT_CORE set to 0
Jan  5 23:37:13 USBKarmic kernel: [  977.962969] Aborting core

(ignore the hostname - it is a lucid install, upgraded from karmic. I haven't figured out how to change the name yet)

Any clues?

Actually, now that I look more closely at syslog I am getting

Jan  5 23:22:22 USBKarmic kernel: [   86.742005] hald-probe-inpu[2581]: segfault at fffffffffffffffe ip 00007f07c3b2ae39 sp 00007fff04481800 error 4 in libc-2.10.2.so[7f07c3aaf000+166000]
Jan  5 23:22:22 USBKarmic kernel: [   86.742026] Process 2581(hald-probe-inpu) has RLIMIT_CORE set to 0
Jan  5 23:22:22 USBKarmic kernel: [   86.742029] Aborting core

as well

---

### Post by paul_in_london on 2010-01-05
+1

I get:

```
paul@lucid:~$ gksu synaptic
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot paul@lucid:~$
```

Among other things, I also get this with the **iron** browser actually, but it doesn't stop it from running.

---

### Post by darco on 2010-01-05
Just updated via command line...recvd this error message:
(I also recvd a similar error message yesterday but all was good)

```
E: Problem executing scripts DPkg::Post-Invoke 'if [ -x /usr/sbin/localepurge ] && [ $(ps w -p $PPID | grep -c remove) != 1 ]; then /usr/sbin/localepurge; else exit 0; fi'
E: Sub-process returned an error code

```

also synaptic pkg manager will not open as well:
```
Gtk:ERROR:/build/buildd/gtk+2.0-2.19.2/gtk/gtkrbtree.c:1098:_gtk_rbtree_find_offset: assertion failed: (tree)
Aborted

```

---

### Post by ranch hand on 2010-01-05
I did this to a couple of my "throw away" versions.

By updating this OS with synaptic and not allowing gtk related updates (mostly) I still have synaptic up and running.

To anyone who has not yet screwed their synaptic here are the updates to avoid;
> 
gtk2-engines-pixbuf libgail-common libgail18 libgksu2-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev
After screwing synaptic on the other installs I used it here and just went a few selections at a time and tried marking them for upgrade.  A box opens if other things are to be marked also.  Avoid the ones above and you should be cool.

I have a couple more OS' to do so I better get at it.

---

### Post by cariboo on 2010-01-05
I just updated, so I didn't realize that synaptic was broken until I saw this thread. When I try starting synaptic from the command line I get this error:

```
sudo synaptic
[sudo] password for me: 
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.19.2/gtk/gtkrbtree.c:1098:_gtk_rbtree_find_offset: assertion failed: (tree)
Aborted

```

aptitude seems to work.

---

### Post by k3lt01 on 2010-01-05
It also affects Computer Janitor as well so it is something to do with them both. If you try to start Computer Janitor it may create a Bug Report(#503656) which may help the devs fix the issue quickly.

---

### Post by ubername on 2010-01-06
Fixed with latest updates

---

### Post by paul_in_london on 2010-01-06
Confirmed fixed. The updates were a little slow coming through for me, even though I'm using the main server.

---

### Post by Eclipse. on 2010-01-06
> **ranch hand said:**
> I did this to a couple of my "throw away" versions.

By updating this OS with synaptic and not allowing gtk related updates (mostly) I still have synaptic up and running.

To anyone who has not yet screwed their synaptic here are the updates to avoid;
After screwing synaptic on the other installs I used it here and just went a few selections at a time and tried marking them for upgrade.  A box opens if other things are to be marked also.  Avoid the ones above and you should be cool.

I have a couple more OS' to do so I better get at it.

Why go to all the bother of more than one testing system? Seems like serious overkill.

---

### Post by ranch hand on 2010-01-06
I test a number of things and one 10.04 is my daytime production OS.  I want it up and running.

I do not spend much time with the others, they are there to see if they work.

My ATI video card works great as long as you are happy, as I am, with the generic driver and no desktop effects.  One of my other OS' has the xorg.edgers stuff on it (doesn't work real well on here but it does work.  I have OOo3.2 on another OS.  9.10>10.04 upgrade of minimal with gnome desktop environment. 9.04>9.10>10.04 upgrade of a respin (some problems with that one).

This is not in any way testing over kill.  I probably is playing with the buggers over kill.

I have myself convinced that it is educational and we all know that is good.

---

