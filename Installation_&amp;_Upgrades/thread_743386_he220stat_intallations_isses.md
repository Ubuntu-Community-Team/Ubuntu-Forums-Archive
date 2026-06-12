---
title: "he220stat intallations isses"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Mudithaktg on 2008-04-02
hi all, 
I am bit new to unix. I am using ubuntu. i am working with Huawei E220 modem. i am tring to install he220stat. according to the readme file 
i) in did ./configure
the next step is execute 'make' command. But when i running that it gets errors, fallowing my error log

/he220stat-0x03# make
gcc -Wall -lncurses init_ncurses.c main.c flowreport.c rssi.c modechange.c -o he220stat
/tmp/ccoSM0JK.o: In function `init_ncurses':
init_ncurses.c : (.text+0xe): undefined reference to `initscr'
init_ncurses.c : (.text+0x13): undefined reference to `noecho'
init_ncurses.c : (.text+0x1f): undefined reference to `halfdelay'
init_ncurses.c : (.text+0x2b): undefined reference to `curs_set'
init_ncurses.c : (.text+0x30): undefined reference to `stdscr'
init_ncurses.c : (.text+0x39): undefined reference to `stdscr'
init_ncurses.c : (.text+0x58): undefined reference to `stdscr'
init_ncurses.c : (.text+0x61): undefined reference to `stdscr'
init_ncurses.c : (.text+0x9f): undefined reference to `newwin'
init_ncurses.c : (.text+0xb1): undefined reference to `wclear'
init_ncurses.c : (.text+0xce): undefined reference to `wprintw'
init_ncurses.c : (.text+0xf2): undefined reference to `newwin'
init_ncurses.c : (.text+0x11b): undefined reference to `newwin'
init_ncurses.c : (.text+0x144): undefined reference to `newwin'
init_ncurses.c : (.text+0x15e): undefined reference to `wprintw'
init_ncurses.c : (.text+0x173): undefined reference to `wprintw'
init_ncurses.c : (.text+0x188): undefined reference to `wprintw'
/tmp/cc9Unprd.o : In function `main':
main.c: (.text+0xa1): undefined reference to `printw'
main.c: (.text+0x1a8): undefined reference to `wrefresh'
main.c: (.text+0x1b5): undefined reference to `wrefresh'
main.c: (.text+0x1c2): undefined reference to `wrefresh'
main.c: (.text+0x1cf): undefined reference to `wrefresh'
main.c: (.text+0x1d4): undefined reference to `stdscr'
main.c:(.text+0x1dc): undefined reference to `wgetch'
main.c:(.text+0x203): undefined reference to `endwin'
/tmp/cckJe5FQ.o: In function `flowreport':
flowreport.c: (.text+0x53): undefined reference to `wclear'
flowreport.c: (.text+0xc2): undefined reference to `wprintw'
flowreport.c : (.text+0xcf): undefined reference to `wrefresh'
/tmp/ccvB3udz.o: In function `rssi':
rssi.c : (.text+0x31): undefined reference to `delwin'
rssi.c : (.text+0x3e): undefined reference to `wclear'
rssi.c : (.text+0x5b): undefined reference to `wprintw'
rssi.c : (.text+0x9b): undefined reference to `newwin'
rssi.c : (.text+0xad): undefined reference to `wclear'
/tmp/ccYWkEJp.o: In function `modechange':
modechange.c : (.text+0x3a): undefined reference to `wprintw'
modechange.c : (.text+0x6e): undefined reference to `wprintw'
modechange.c : (.text+0xaa): undefined reference to `wprintw'
modechange.c : (.text+0xc0): undefined reference to `wrefresh'
collect2: ld returned 1 exit status
make: *** [all] Error 1

According to one forums advice i did followings, 
sudo apt-get update
sudo apt-get install build-essential 
those were successful but when i try to run 'make' above errors are still coming.

Please help me to solve this issue.

Thnkx
Muditha

---

### Post by oozie on 2008-04-03
Make sure you have all of these packets installed.
build-essential / ncurses / ncurses-dev / xterm

It looks to me that you miss ncurses itself.

Good Luck

---

