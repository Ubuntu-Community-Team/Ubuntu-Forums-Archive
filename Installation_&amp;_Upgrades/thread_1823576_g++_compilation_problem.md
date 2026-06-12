---
title: "g++ compilation problem"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by vptl316 on 2011-08-12
Hi,

I installed g++ using package manager and support libraries using 
sudo apt-get install build-essential cmd,
but I'm not able to compile a socket code.
It gives me the following error:

server.cpp:1:26: error: ServerSocket.h: No such file or directory
server.cpp:2:29: error: SocketException.h: No such file or directory

Can Anyone tell me what's wrong?!!:confused:

---

### Post by lkraemer on 2011-08-12
SocketException.h should be a clue.... you need your Headers.......

[B]
INSTALL REQUIRED SOFTWARE FOR COMPILE:[/B]
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.   .........


You most likely will also want to install:
> 
gdb 
ddd

also.....

lk

---

