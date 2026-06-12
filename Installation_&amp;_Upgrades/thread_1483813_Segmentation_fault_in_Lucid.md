---
title: "Segmentation fault in Lucid"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by alefisico on 2010-05-15
Hi everyone.
I had just upgrade my ubuntu Karmic to Lucid. Before this upgrade, my computer worked pretty well but after this I could not run some applications like VI or empathy. 
When I tried to open a text file with VI appears this message:
```

ale@Gluon:~$ vi prueba
Vim: Caught deadly signal SEGV
Segmentation fault

```
Have anybody an idea of what could it happen??

---

### Post by immeëmosol on 2010-11-14
Traced mine down to having trouble with middle-mouse-click( i think).

Maybe you can confirm it is on middlemoueclick-copy-paste-action ?


What you may also want to try is start vim with gdb( The GNU Debugger).
For instance, i editted ~/.bashrc so normally i would've typed:
```

$ vim ~/.bashrc

```
but for gdb it will become:
```

$ gdb vim
(gdb) set args ~/.bashrc
(gdb) run

```
Then if i try the middlemouseclik paste from selected text in vim( in gnome-terminal) i get:
```

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff440ca9e in memcpy() from /lib/libc.so.6

```
And mouseclicks in that gnome-terminal shell do no longer work, instead they show text-sequences on the prompt.

(( On ubuntu 10.10-64. ))

---

