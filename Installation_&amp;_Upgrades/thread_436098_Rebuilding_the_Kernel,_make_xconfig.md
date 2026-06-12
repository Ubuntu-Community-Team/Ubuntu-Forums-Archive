---
title: "Rebuilding the Kernel, make xconfig"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by jdelasalas on 2007-05-07
I'm new to rebuilding the Kernel in ubuntu.  Whenever I use the command xconfig, I get the following slew of errors:

  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
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

am I skipping a step?

---

### Post by hal8000 on 2007-05-07
n file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory

Have you installed ncurses and the kernel source?

You can also use make menuconfig to configure the kernel. Have you tried this and do you get the same errors?

---

### Post by iSYS on 2007-10-27
Looks like my problem was with qt3.  If others are having problems, check into qt3.

---

