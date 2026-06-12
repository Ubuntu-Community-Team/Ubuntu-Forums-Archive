---
title: "Question about building kernel"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by g320907aa on 2008-06-17
Hello, anyone has an experience building a kernel for 7.04 or 7.10/8.04? 
I would need to do it and found out that it takes about 8hours to do a single build. I want to insert some debugging messsages into the kernel and just wanna be able to build only the modified part not the clean build. Is it possible to do? Has anyone done it? THanks!

---

### Post by g320907aa on 2008-06-17
hmm, no one can answer it? or is it wrong place to post?

---

### Post by ByteJuggler on 2008-06-17
I haven't built a kernel in ages, but you'll have to compile everything at least once, which will take as long as it will take.  Once that's done, the makefiles and such will ensure you can rebuild/relink a new kernel quickly, only recompiling the modules you've edited and relinking the object files from the previous build without recompiling them if their corresponding source files haven't changed.  

As for you how long, I don't remember it taking quite that long, even several years ago when I last did that, and today's machines are quicker than back then, so I wouldn't expect it to take 8 hourse.. (more like, say 20 mins or 30 mins, finger in the wind general estimate for a semi decent machine.)

---

### Post by moore.bryan on 2008-06-17
i've done it in the past and saw negligible, if any, advantages; any reason why you're taking this on?

---

### Post by g320907aa on 2008-06-17
> **moore.bryan said:**
> i've done it in the past and saw negligible, if any, advantages; any reason why you're taking this on?

i have vt8251 via sb on which the live cd wont boot from sata drive. (i have another post regarding this issue and this issue seems to be quite common on via chipsets) 

now i downloaded the whole source code and found the VIA ATA initialiation related code and wanna put some debugging output to get close view on what is happening.

---

### Post by g320907aa on 2008-06-17
btw instruction below seems to be completely useless or out of date or both. None of the commands will work. 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Can someone point me to step by step direction for compiling?
my system is using 7.10 with 2.6.22.

---

### Post by g320907aa on 2008-06-17
ok i used the old fashioned way like follows: 

sudo apt-get install linux-source
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2
cd linux-source-<version-number-here>

but running 
make menuconfig, i got  this:

root@tester-desktop:/usr/src/linux-source-2.6.22# make menuconfig
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before ‘chtype’
scripts/kconfig/lxdialog/dialog.h:187: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:194: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:196: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:197: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:198: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:199: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:201: error: expected ‘)’ before ‘*’ token
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

if i run run
make xconfig



root@tester-desktop:/usr/src/linux-source-2.6.22# make xconfig
  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2

seems like some library seem to be missing. anyone has clue?

---

### Post by g320907aa on 2008-06-18
ok i was able to build the kernel, the above error was due to missing packages for xconfig. 
Now the trouble is, the place I should look at is actually initrd not the kernel itself althought it might still be useful.
juggler/bryan have you guys dealth with the initrd?
What I would like to do is get the source for initrd image ( I was actually acquire the binary and look inside it) and hopefully built and replaced the current one either on CD or on system. Thanks!

---

### Post by moore.bryan on 2008-06-18
unfortunately, it's been so long, i'm not sure; sorry...
::shrug::

---

### Post by g320907aa on 2008-06-19
ok i was able to do everything i needed. 
bult and installed successfully. i also had to create separate initrd image as well as separate /lib/module folder. Once it is done, i could boot with the newly built kernel.

---

### Post by ByteJuggler on 2008-06-19
Excellent glad you got it sorted.  You might want to post a summary of what you did for other's benefit in the future (when they view this thread) including the initrd image stuff.  You might also want to mark the thread as  solved.

Cheers!

---

### Post by finite9 on 2008-06-19
If you want some good tips for compiling kernels do a google for "howto compile kernel Ubuntu" and click on the HOWTO Forge links.  I have successfully compiled kernels for CentOS, Debian and Ubuntu (Dapper Drake) using this site.

---

