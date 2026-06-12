---
title: "Problem with Xtrlock compiling with new hide command"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by antoniospider on 2013-05-18
[COLOR=#000000][INDENT]Greeting to all people it's a pleasure to be here !!
i'm Antonio 
i would like to ask you all a question ...

I found a patch [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=571985](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=571985)
which adds two command-line options to xtrlock:

--forever: completely disables unlocking

--hide-cursor: makes the mouse cursor invisible


**How do I use this patch?**

P.S. I don't know much about compiling.

i also found this one called "better xtrlock" but i can't compile it ...
can someone give some explanation about it ??
i've tried with
gcc -o filename file.c 
but it returns me some error before it can creates and executable file
[https://github.com/jaseg/Better-XTrLock](https://github.com/jaseg/Better-XTrLock)

Thanks to all in advance and have a nice day ![/INDENT]


[/COLOR]

---

### Post by antoniospider on 2013-05-18
it is a very useful application because it allows me to show some stuff on my monitors in my agency but i'd want to "hide" that cursor because it don't permits people to see clearly what is on the monitor ... i use the terminals as a "read only" support and to prevents some damage i found this great application that lock mouse and keyboard with pw . let me know ! thanks . antonio

---

### Post by antoniospider on 2013-05-18
sry if it's the wrong section
i've just found the " absolute beginners" section and i think it could be there

---

### Post by antoniospider on 2013-05-18
Anyone with some good suggestion ?? Thanks a lot

---

### Post by steeldriver on 2013-05-18
It's hard to give specific advice about compiling random bits of software - especially when you don't post the exact errors you're getting 

If you want to patch the first source, have a read here --> [http://jungels.net/articles/diff-patch-ten-minutes.html](http://jungels.net/articles/diff-patch-ten-minutes.html)

However if you decide to have a go at building the [COLOR=#000000]"better xtrlock" then have a look first to see if it comes with a README or INSTALL file - if it just comes with a Makefile, then you can try typing

```
make
```
[/COLOR]
instead of using gcc directly (the Makefile should define a sensible default target and know how to build it). If you get errors and can't figure them out then post back. Good luck.

---

### Post by antoniospider on 2013-05-19
ok thanks a lot [COLOR=#000000]steeldriver [/COLOR]i'm going to try it and report it back !

---

### Post by antoniospider on 2013-05-20
so i've tried to execute the "make" command after downloading better xtrlock and it returns me back an error :
"xtrlock.c:19:19 fatatl error : X11/X.h : No such file or directory compilation terminated.
make : *** [xtrlock.o] Error 1 "

---

### Post by antoniospider on 2013-05-20
**update**
i've tried to install the libx11-dev from the ubuntu software center , it returns me back an error 
"depends libx11-6 (=2:1.4.99 1-0ubuntu2) but 2:1.4.99.1 0ubuntu2 is to be installed .

so i searched for the xlib11-6 lib and found it as installed . 
:)
i have ubuntu 12.04 with the lasts update .
the fact is that i've tried to run the better xtrlock on backtrack r2 (on a virtual machine) and it went up in a while . 
thanks in advance! antonio

---

### Post by stinkeye on 2013-05-20
I can install Better-XTrLock from the link in your first post. I'm on  raring 13.04.
[https://github.com/jaseg/Better-XTrLock](https://github.com/jaseg/Better-XTrLock)

Locks the screen without the cursor image.

I already had xtrlock installed from the repos so uninstalled first.(probably not necessary)
Installed build tools...
```
sudo apt-get install build-essential gcc
```

Downloaded the [Better-XTrLock zip]("https://github.com/jaseg/Better-XTrLock/archive/master.zip")  and extracted to my home folder.

Opened a terminal and ran...
```
cd Better-XTrLock-master
sudo make install
```

Now installed.

---

### Post by antoniospider on 2013-05-20
thanks stinkeye for the answer 
i-ve just tried to follow your instructions installing the build essential too
here the response 

~/Desktop/Better-XTrLock-master$ sudo make install
gcc -Wall -DSHADOW_PWD   -c -o xtrlock.o xtrlock.c
xtrlock.c:19:19: fatal error: X11/X.h: No such file or directory
compilation terminated.
make: *** [xtrlock.o] Error 1

---

### Post by stinkeye on 2013-05-20
> **antoniospider said:**
> thanks stinkeye for the answer 
i-ve just tried to follow your instructions installing the build essential too
here the response 

~/Desktop/Better-XTrLock-master$ sudo make install
gcc -Wall -DSHADOW_PWD   -c -o xtrlock.o xtrlock.c
xtrlock.c:19:19: fatal error: X11/X.h: No such file or directory
compilation terminated.
make: *** [xtrlock.o] Error 1

Don't know enough to fix your issue... just thought I would see if it would install here.
If your only issue is the lock showing, maybe install xtrlock from repos.
Then move the mouse while locking.(needs xdotool)
eg 
```
xdotool mousemove 0 0 && xtrlock
```

---

### Post by antoniospider on 2013-05-20
it's really strange because as i said i downloaded the same better xtrlock and install it on backtrack (on virtual machine) execute it and everithing good ... hope to solve the ting . thanks to all ! antonio

---

### Post by stinkeye on 2013-05-20
One package I have, that is not included by default is
**libx11-dev**
```
sudo apt-get install libx11-dev
```

---

### Post by antoniospider on 2013-05-20
> **stinkeye said:**
> Don't know enough to fix your issue... just thought I would see if it would install here.
If your only issue is the lock showing, maybe install xtrlock from repos.
Then move the mouse while locking.(needs xdotool)
eg 
```
xdotool mousemove 0 0 && xtrlock
```

hope to fix with better xtrlock because i need to lock the monitor but not show the mouse either with the transparency or hiding mode so that package was perfect . i'm just trying with a new installation of ubuntu 13.04 i386 clear, installing betterxtrlock and compiling the libx11 dependencies . if anyone has some good suggestions everything welcome :) thanks ! antonio

---

### Post by antoniospider on 2013-05-20
***UPDATED****
______SOLVED_____

Greets !
After erasing the disk and formatting with ubuntu 13.04 amd64 

- i installed the build essential packages gcc 
- _Modified the update repository changing from source "italy" to main server_
- Now i can download the[FONT=Ubuntu Mono, monospace][COLOR=#000000] libx11-dev from the repository 
- Download the better xtrlock from the github site compile it with "make " then "make install" with sudo option 
- Launch the application with   xtrlock 

Thanks to Steeldriver and Stinkeye for the support !! have a nice day [/COLOR][/FONT]

---

