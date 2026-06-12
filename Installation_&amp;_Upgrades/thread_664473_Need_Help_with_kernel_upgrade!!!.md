---
title: "Need Help with kernel upgrade!!!"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by blackenedbloodx on 2008-01-11
Ok, i am trying to upgrade my kernel because of the kacpid problem. (search google for "kacpid" if u need more info.)  And one thing i keep hearing is that if they downgrade or upgrade their kernel, it fixes. must be a bug. so i downloaded a newer kernel from zen. i ran the make command and this is what it gave me. any clues? how do i configure my kernel?

blackenedblood@HellzGate:~$ cd /home/blackenedblood/Downloads/kernel/zen-sources
blackenedblood@HellzGate:~/Downloads/kernel/zen-sources$ make
scripts/kconfig/conf -s arch/x86/Kconfig
***
*** You have not yet configured your kernel!
*** (missing kernel .config file)
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.

---

### Post by PmDematagoda on 2008-01-11
You may use:-
```
sudo make menuconfig
```
or
```
sudo make xconfig
```
to make the config file.

---

### Post by blackenedbloodx on 2008-01-11
blackenedblood@HellzGate:~$ sudo make menuconfig
[sudo] password for blackenedblood:
make: *** No rule to make target `menuconfig'.  Stop.
blackenedblood@HellzGate:~$ sudo make xconfig
make: *** No rule to make target `xconfig'.  Stop.

---

### Post by PmDematagoda on 2008-01-11
I believe you would have to execute the command in the folder containing the kernel source to be compiled. Move to that folder and try the commands again.

---

### Post by blackenedbloodx on 2008-01-11
D'oh! can't believe i didnt think abt taht!!! k but stick around just in case ok?

EDIT: 
yup. more errors. sorry its a little lengthy but im not in control of that :D

  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before &#8216;chtype&#8217;
scripts/kconfig/lxdialog/dialog.h:187: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:194: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:196: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:197: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:198: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:199: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:201: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c: In function &#8216;dialog_checklist&#8217;:
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;dialog&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;list&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function &#8216;getmaxy&#8217;
scripts/kconfig/lxdialog/checklist.c:129: error: &#8216;stdscr&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: &#8216;KEY_MAX&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function &#8216;getmaxx&#8217;
scripts/kconfig/lxdialog/checklist.c:137: error: &#8216;COLS&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: &#8216;LINES&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function &#8216;draw_shadow&#8217;
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function &#8216;newwin&#8217;
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function &#8216;keypad&#8217;
scripts/kconfig/lxdialog/checklist.c:143: error: &#8216;TRUE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function &#8216;draw_box&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function &#8216;wattrset&#8217;
scripts/kconfig/lxdialog/checklist.c:147: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function &#8216;mvwaddch&#8217;
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function &#8216;waddch&#8217;
scripts/kconfig/lxdialog/checklist.c:151: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function &#8216;print_title&#8217;
scripts/kconfig/lxdialog/checklist.c:156: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function &#8216;print_autowrap&#8217;
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function &#8216;subwin&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function &#8216;print_item&#8217;
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function &#8216;print_arrows&#8217;
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function &#8216;print_buttons&#8217;
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function &#8216;doupdate&#8217;
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function &#8216;wgetch&#8217;
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: &#8216;FALSE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function &#8216;scrollok&#8217;
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function &#8216;wscrl&#8217;
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function &#8216;wrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function &#8216;delwin&#8217;
scripts/kconfig/lxdialog/checklist.c:297: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function &#8216;on_key_esc&#8217;
scripts/kconfig/lxdialog/checklist.c:312: error: &#8216;KEY_RESIZE&#8217; undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2


And here's the other one

  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2

---

