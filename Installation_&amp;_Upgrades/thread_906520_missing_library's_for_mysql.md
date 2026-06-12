---
title: "missing library's for mysql"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-08-31
hello

I try'd to compile mysql 5.1. but i got an error bij the *# ./configure --prefix=/opt/gdxweb/mysql --with-mysql-user=mysql *command. I got the error that the curses/termcap library was missing. I found on forums that i needed to instal ncurses-dev so i did but the error stil comes up.

is there an solution?

*i am sorry for my bad english*

Robbert

---

### Post by kellemes on 2008-08-31
Is **libncurses5-dev** the package you installed?
As far as I know this is what you need.

---

### Post by herrbrand on 2008-08-31
yes thats the pakage i instald. but it was already instald.

---

### Post by herrbrand on 2008-09-01
hello

I solved the problem. I just installed the tremcap library it self from: [http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm)
in the terminal you just type:
./configure <enter>
make
make instsall

new I can compile mysql

Robbert

---

