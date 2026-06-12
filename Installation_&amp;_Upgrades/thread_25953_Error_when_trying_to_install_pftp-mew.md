---
title: "Error when trying to install pftp-mew"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by xebitx on 2005-04-11
Okay I edited the config and did

sudo ./configure
sudo make dynamic

and then I get this:

martin@ubuntu:/usr/bin/pftp-mew/pftpfxp-mew$ sudo make dynamic
cd src;make dynamic;cd ..
make[1]: Entering directory `/usr/bin/pftp-mew/pftpfxp-mew/src'
g++ -c -Wall -D_REENTRANT -I../include -O2 main.cc
main.cc:4:20: curses.h: No such file or directory
main.cc:5:19: panel.h: No such file or directory
In file included from main.cc:13:
../include/tcp.h: In member function `void CTCP::ResetMessage()':
../include/tcp.h:83: error: `FALSE' undeclared (first use this function)
../include/tcp.h:83: error: (Each undeclared identifier is reported only once
   for each function it appears in.)
In file included from main.cc:14:
../include/server.h: In member function `void CServer::SetTransfering()':
../include/server.h:151: error: `TRUE' undeclared (first use this function)
In file included from main.cc:15:
../include/displayhandler.h: At global scope:
../include/displayhandler.h:47: error: syntax error before `*' token
../include/displayhandler.h:51: error: syntax error before `*' token
../include/displayhandler.h:68: error: type specifier omitted for parameter `
   WINDOW'
../include/displayhandler.h:68: error: parse error before `*' token
../include/displayhandler.h:69: error: type specifier omitted for parameter `
   WINDOW'
../include/displayhandler.h:69: error: parse error before `*' token
../include/displayhandler.h:72: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:72: error: `window' was not declared in this scope
../include/displayhandler.h:72: error: invalid data member initialization
../include/displayhandler.h:72: error: (use `=' to initialize static data
   members)
../include/displayhandler.h:72: error: variable or field `
   UpdateFilelistNewPosition' declared void
../include/displayhandler.h:76: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:76: error: parse error before `,' token
../include/displayhandler.h:78: error: type specifier omitted for parameter `
   WINDOW'
../include/displayhandler.h:78: error: parse error before `*' token
../include/displayhandler.h:199: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:199: error: parse error before `)' token
../include/displayhandler.h:212: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:212: error: parse error before `,' token
../include/displayhandler.h:213: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:213: error: parse error before `,' token
../include/displayhandler.h:262: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:262: error: parse error before `)' token
../include/displayhandler.h:288: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:288: error: `win' was not declared in this scope
../include/displayhandler.h:288: error: variable or field `mywborder' declared
   void
main.cc:53: error: `WINDOW' was not declared in this scope
main.cc:53: error: `win' was not declared in this scope
main.cc:53: error: variable or field `mywborder' declared void
main.cc:53: error: redefinition of `int mywborder'
../include/displayhandler.h:288: error: `int mywborder' previously defined here
main.cc:53: error: syntax error before `{' token
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/usr/bin/pftp-mew/pftpfxp-mew/src'


Can someone tell me what the problem is?

---

### Post by xebitx on 2005-04-11
Found the problem, I just needed to install ncurses :)

---

