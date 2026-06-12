---
title: "Kernel Compiling"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Phantom784 on 2007-06-09
I want to be able to use the "rope" matching module on one of my ubuntu machines.  ([http://www.lowth.com/rope/](http://www.lowth.com/rope/)).  To install it, you need to recompile the kernel.  I found directions on compiling the kernel for ubuntu on this website ([http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)).  It includes directions on when you should patch the kernel.  However, I need to know if there are any other patches that have to be applied to the ubuntu kernel at this stage in order for Ubuntu to work.  Also, will using a kernel with this patch for rope break binary compatibility of already installed software on my machine?

Also, I was wondering why some kernel-level modifications can simply be done as plugins that you can compile and then modprobe in, but others, such as ropes, require recompiling the kernel?

---

### Post by 444 on 2007-06-09
sudo apt-get install linux-source
Will get you the kernel source with the Ubuntu patches included.

iptables appears to be in modules in Ubuntu so you may not need to recompile the whole kernel, just the modules involved.

So you'd apply the patch to the ubuntu source, then copy the Ubuntu kernel config from /boot, and run 'make oldconfig'. Then you'd run 'make so-and-so-module' and just copy the modified modules over.

---

### Post by Phantom784 on 2007-06-09
Ropes was giving me lots of problems, and not just with the kernel, so i decided to use the usespace Layer 7 program instead.  It, however, still requires a new kernel, but this time just with some options changed, not a new module or patch or anything.  So I follow all the directions on the HowTo page I linked to in my first post (except using the source from the repos instead of kernel.org), and it works until the "make menuconfig" command.  It fails with this output.

```
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before ‘chtype’
scripts/kconfig/lxdialog/dialog.h:187: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:193: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:195: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:196: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:197: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:198: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:200: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:31: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:59: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:95: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c: In function ‘dialog_checklist’:
scripts/kconfig/lxdialog/checklist.c:116: error: ‘WINDOW’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: ‘dialog’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: ‘list’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function ‘getmaxy’
scripts/kconfig/lxdialog/checklist.c:129: error: ‘stdscr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: ‘KEY_MAX’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function ‘getmaxx’
scripts/kconfig/lxdialog/checklist.c:137: error: ‘COLS’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: ‘LINES’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function ‘draw_shadow’
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function ‘newwin’
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function ‘keypad’
scripts/kconfig/lxdialog/checklist.c:143: error: ‘TRUE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function ‘draw_box’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function ‘wattrset’
scripts/kconfig/lxdialog/checklist.c:147: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function ‘mvwaddch’
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function ‘waddch’
scripts/kconfig/lxdialog/checklist.c:151: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function ‘print_title’
scripts/kconfig/lxdialog/checklist.c:156: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function ‘print_autowrap’
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function ‘subwin’
scripts/kconfig/lxdialog/checklist.c:171: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:171: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function ‘print_item’
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function ‘print_arrows’
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function ‘print_buttons’
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function ‘wnoutrefresh’
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function ‘doupdate’
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function ‘wgetch’
scripts/kconfig/lxdialog/checklist.c:210: error: ‘KEY_UP’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: ‘KEY_DOWN’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: ‘FALSE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function ‘scrollok’
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function ‘wscrl’
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function ‘wrefresh’
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function ‘delwin’
scripts/kconfig/lxdialog/checklist.c:297: error: ‘KEY_LEFT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: ‘KEY_RIGHT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function ‘on_key_esc’
scripts/kconfig/lxdialog/checklist.c:312: error: ‘KEY_RESIZE’ undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

Does anyone know how to get the configuration utility up?  I can't just use oldconfig because I want to use a different configuration.  The directions on what I need to change are on this page ([http://l7-filter.sourceforge.net/HOWTO-userspace#Doing](http://l7-filter.sourceforge.net/HOWTO-userspace#Doing)), under Kernel.

---

### Post by Phantom784 on 2007-06-09
Apparently, I didn't have the ncurses5-dev package installed.  Installed it and it worked perfectly.

---

