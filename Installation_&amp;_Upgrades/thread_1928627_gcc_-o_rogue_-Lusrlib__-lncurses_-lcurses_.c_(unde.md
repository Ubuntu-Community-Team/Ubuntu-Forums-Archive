---
title: "gcc -o rogue -L/usr/lib/  -lncurses -lcurses *.c (undefined ref)"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by xmorg on 2012-02-20
Hi,

Im playing around with C and making a roguelike but I cant get it to compile in ubuntu.

I have searched around, and basically the consensis is to do -lncurses when compiling.

I have done that.  My original compile string is gcc -lncurses *.c, which worked fine in freebsd.

I added the -L/usr/lib thinking maybe it couldnt find the lib
I also added -lcurses, basically trying anything i could think of

what happens are about 3 pages of undefind refernce errors to pretty much every curses function im calling, and functions that those functions call.

examples

actors.c:(.text+0x403): undefined reference to `stdscr'
actors.c:(.text+0x40b): undefined reference to `wclear'
actors.c:(.text+0x410): undefined reference to `noecho'
actors.c:(.text+0x415): undefined reference to `cbreak'
actors.c:(.text+0x439): undefined reference to `mvprintw

i have installed ncurses-base, libncurses5, libncurses, libncursesw5, libnurses5-dev.  why is it so hard to compile a basic program using ncurses?  If i ever wanted to distribute it, i wouldnt want users to have to reseach how to build...

---

### Post by cbob on 2012-02-20
Hi,

If you have not, try installing the dev-component of ncurses.
```
apt-get install ncurses-dev
```Regards,
cbob

---

### Post by cbob on 2012-02-20
Also i see now that you pass the library link in the middle of the compile command, this may be the source of the failure, you need to pass the link parameter at the end of the command:
```
gcc *.c -lncurses
```/cbob

---

