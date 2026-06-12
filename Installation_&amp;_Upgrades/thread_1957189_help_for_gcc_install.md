---
title: "help for gcc install"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by saeid6366 on 2012-04-12
Hi friends
i'm a beginner in linux and ubuntu.
i want to install gcc-4.7.0 of source
i dont have problem with configure it. and it create makefile 
but when i make it, i'm faced with a cycle.
i waited for 1 hour but did not stop and showed duplicate messages
i'm confused :confused:
plz help me

---

### Post by kc1di on 2012-04-12
Hi Without more information it would be hard to say what is causing the cycle as you call it.   are there any make error messages in the terminal?

It may be much easier for you to install the PPA repository and install GCC 4.7 from there.   I'm not sure which version of Ubuntu your using.

Here is a web page that may be of help to you:

[http://askubuntu.com/questions/113291/installing-gcc-4-7]("http://askubuntu.com/questions/113291/installing-gcc-4-7")
(NOTE: GCC-4.7 has only been packaged for Ubuntu 12.04 so far) so this will only work if your running that verison of Ubuntu.  I suspect that if your using an older version that may be the reason your haveing problems with make.

Let us know how you make out

---

### Post by codemaniac on 2012-04-12
Hello , can you please post the "duplicate messages" that you are getting while installation ?

---

### Post by saeid6366 on 2012-04-12
> **kc1di said:**
> Hi Without more information it would be hard to say what is causing the cycle as you call it.   are there any make error messages in the terminal?

It may be much easier for you to install the PPA repository and install GCC 4.7 from there.   I'm not sure which version of Ubuntu your using.

Here is a web page that may be of help to you:

[http://askubuntu.com/questions/113291/installing-gcc-4-7]("http://askubuntu.com/questions/113291/installing-gcc-4-7")
(NOTE: GCC-4.7 has only been packaged for Ubuntu 12.04 so far) so this will only work if your running that verison of Ubuntu.  I suspect that if your using an older version that may be the reason your haveing problems with make.

Let us know how you make out

I have ubuntu 11.10
but i when a older version of gcc like gcc-4.6.2 i recieve this error:

In file included from /usr/include/stdio.h:28:0,
        
         from /home/hallaji/gcc-4.6.2/libgcc/../gcc/tsystem.h:87,
       
          from /home/hallaji/gcc-4.6.2/libgcc/../gcc/libgcc2.c:29:
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.

make[3]: *** [_muldi3.o] Error 1
make[3]: Leaving directory `/home/hallaji/gcc/i686-pc-linux-gnu/libgcc'

make[2]: *** [all-stage1-target-libgcc] Error 2
make[2]: Leaving directory `/home/hallaji/gcc'

make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/hallaji/gcc'
make: *** [all] Error 2


what is PPA repository?

---

### Post by saeid6366 on 2012-04-12
> **codemaniac said:**
> Hello , can you please post the "duplicate messages" that you are getting while installation ?

I can't stop it. how can i copy these messages?
but i know that these are checking message

---

### Post by kc1di on 2012-04-12
> **saeid6366 said:**
> I have ubuntu 11.10
what is PPA repository?

PPA stands for Personal Package Archive (it's a personal repository that works with ubuntu and debian packages.) 

The one I sent you is only for version 12.04 so it will not work to install gcc 4.7 on 11.10- sorry.  I suspect though that your missing a dependency or there is a directory that gcc 4.7 is looking for and can not find in 11.10.  However can't be of much further help to you but someone should have the answer.
one possibility if your really need gcc 4.7 is to upgrade to 12.04 it will be released soon and is already quite stable.

---

### Post by saeid6366 on 2012-04-12
> **kc1di said:**
> PPA stands for Personal Package Archive (it's a personal repository that works with ubuntu and debian packages.) 

The one I sent you is only for version 12.04 so it will not work to install gcc 4.7 on 11.10- sorry.  I suspect though that your missing a dependency or there is a directory that gcc 4.7 is looking for and can not find in 11.10.  However can't be of much further help to you but someone should have the answer.
one possibility if your really need gcc 4.7 is to upgrade to 12.04 it will be released soon and is already quite stable.
thanks a lot for Guidance about PPA

---

### Post by codemaniac on 2012-04-12
what is the current gcc version in your system ?
Please check .
```
gcc --version
```

---

