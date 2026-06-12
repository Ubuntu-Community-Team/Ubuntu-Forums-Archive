---
title: "Installing PuTTY on Hedgehog 5.05"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by kenichiro on 2005-07-23
I am a total NOOB to Linux. I am trying to use this to "console" to my routers. I am also just trying to learn how to install STUFF. I'm coming over from a MS only environment. This stuff seems very frustrating but I know it's only because I don't know the process yet. I did the OS install with no issues. Also, are there other ways to console to routers/switches.

I get the folowing message when I issue the command "make -f Makefile.gtk"


[email]root@ubuntu-svr:/home/admin123/putty-0.58.tar.gz[/email]_FILES/putty-0.58/unix # make -f Makefile.gtk
cc   -O2 -Wall -Werror -g -I.././ -I../charset/ -I../windows/ -I../unix/ -I../mac/ -I../macosx/ `gtk-config --cflags` -c ../be_all.c
/bin/sh: gtk-config: command not found
/bin/sh: cc: command not found
make: *** [be_all.o] Error 127

---

### Post by mike998 on 2005-07-23
you can simply open a Terminal (found under System Tools) and either ```
ssh -l *username* *ipaddress*
```  or ```
telnet [I]ipaddress[/I
``` 
Normally, you don't need putty - it's really only used (for me) under windows.

---

### Post by kenichiro on 2005-07-23
Thanks... I need to connect to network gear thru a console cable connected to my serial port. The devices I connect to have no IP address yet.

---

### Post by Saru san on 2005-07-23
Maybe this will help?
[http://techrepublic.com.com/5208-11186-0.html?forumID=36&threadID=173271](http://techrepublic.com.com/5208-11186-0.html?forumID=36&threadID=173271)

Install minicom with```
$ sudo apt-get install minicom
```

---

