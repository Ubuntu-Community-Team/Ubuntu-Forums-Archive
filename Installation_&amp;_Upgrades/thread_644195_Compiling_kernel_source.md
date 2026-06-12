---
title: "Compiling kernel source"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by pk_sunshine on 2007-12-18
OK I've already installed Ubuntu ver2.6.22-14-server successfully on an old pc with a functional gui and internet conection via proxy (THE BOX I AM SENDING THIS POST FROM).

Now I am trying to install the same version onto a newer ASUS box. However, I have had some issues with the sis190.c not having the correct ISA data, and subsequently not being able to load the correct lan drivers (NO NETWORK :( ).

After much searching and time I found the following very usefull article:
[http://ubuntuforums.org/showthread.php?t=482284]("http://ubuntuforums.org/showthread.php?t=482284")

So now I am trying to compile a new version of the kernel with the corrected sis190.c file on the old pc with the working gui. Then want to copy this new kernel to the new machine 
and hopefully I will have a working network card.

I followed the procedure in this post, but have hit a snag with the command:
sudo make menuconfig

which returns the error:
>   HOSTCC  scripts/kconfig/lxdialog/checklist.o
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





Please help me with this compile step. Am I going to overwrite the kernel on the old machine? I followed the above posts instructions to the letter. I have untared the source, modified the sis190.c file and am now ready to compile.

Thanks in advance.

---

