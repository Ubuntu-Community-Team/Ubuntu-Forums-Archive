---
title: "gcc compiler error for MySQL in Ubuntu Hardy Heron"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by linuxfan84 on 2008-06-17
Hello friends,
               I had installed Ubuntu hardy Heron 8.04 on my laptop using Wubi to compile some server.c and client.c projects for my socket programming project on Linux OS.I was able to view the desired results with the following commands.It's only that when I re-installed Ubuntu and MySQL client-server,I'm getting the following gcc compiler errors that I didn't get before.Please help me out.

user@user-laptop:~/Desktop/project$ gcc –I./mysql/include –L./mysql/lib server.c –o server –lmysqlclient
gcc: –I./mysql/include: No such file or directory
gcc: –L./mysql/lib: No such file or directory
gcc: –o: No such file or directory
gcc: server: No such file or directory
gcc: –lmysqlclient: No such file or directory
server.c:13:19: error: mysql.h: No such file or directory
server.c:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
server.c: In function ‘main’:
server.c:47: error: ‘MYSQL’ undeclared (first use in this function)
server.c:47: error: (Each undeclared identifier is reported only once
server.c:47: error: for each function it appears in.)
server.c:47: error: ‘mysql’ undeclared (first use in this function)
server.c:48: error: ‘MYSQL_RES’ undeclared (first use in this function)
server.c:48: error: ‘result’ undeclared (first use in this function)
server.c:142: error: ‘MYSQL_ROW’ undeclared (first use in this function)
server.c:142: error: expected ‘;’ before ‘row’
server.c:143: error: ‘row’ undeclared (first use in this function)

The above command to compile mysql server worked like a breeze before but now it's giving me the above errors.Please help me out guys.

---

