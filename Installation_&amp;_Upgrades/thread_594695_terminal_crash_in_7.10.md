---
title: "terminal crash in 7.10"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by qmax on 2007-10-28
now, i have all terminals (xterm, gnome-terminal) crashing on startup under gnome.

for xterm:
 _XimParseStringFile. in libX11.so
 _XimLocalOpenIM in libX11.so
 _XimOpenIM in libX11.so

for gnome-terminal:
gconv in in /usr/lib/gconv/iso-8859-1.so

how could i workaround this ?

---

### Post by jenhsun on 2007-10-28
ctrl + Alt + F1 and see what's going on

---

### Post by flobear on 2007-11-05
Hello,

I also have a problem with terminals causing a crash.  When I try to open the terminal from the application menu (Applications/Accessories/Terminal) or if I hit <alt>+<ctrl>+F1, I get a crash.

I'm new to Ubuntu and to Linux in general and I've just installed for the first time.

I'm running Xubuntu 7.10 due to my system's low resources (only 128mb ram).

Any help will be much appreciated.

---

### Post by nandinga on 2007-11-14
Hi, I'm getting the problem also, just with gnome-terminal. I'm using xterm now but...
When I try to execute it from xterm I get:

```
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 111 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

with 0 exit code. I've also reinstalled it with no different results. I can't imagine what can it be... can u help?

---

### Post by blackwell on 2007-11-19
i got this same problem after install gutsy and update 
gnome terminal dotn start

i got it on 2 machines :(

---

### Post by m4him on 2007-12-06
I have the same problem here.  I do not know when it started but this is only my second day of being a convert from XP/Vista.  I did all the updates, added some programs, rebooted, and gnome-terminal crashes when I try to open it.  Xterm works fine.

---

### Post by glthornberry on 2007-12-26
I'm using Xubuntu 7.10.  Mine is only crashing from the GUI, not from Ctl-Alt-F1, etc.  So far no other GUI app is causing the Xorg server to die like this.

What video cards are we all talking about here?  Could this be the common element and the problem is the Xorg server?  

I just installed the machine, but I'm not using it at this moment and I can't provide details.  I do know that it's an Intel chipset and the default server in use is "Intel Experimental".  It is a native server, not proprietary.  Anyone else with this problem using an Intel chipset?

----

I just saw a bug report possibly related to this:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)

Also, a workaround may be to change the default color depth from 24 to 16 in your xorg.conf.  Read through the bugs thread above for some instructions.  I'll give it a try later when I'm in front of the machine!

---

### Post by The_Boot on 2008-05-02
Here's the fix:

[tillamookrage.blogspot.com/2007/09/xfce-terminal-crash-fix.html]("tillamookrage.blogspot.com/2007/09/xfce-terminal-crash-fix.html")

We're still working on what the exact cause is, whether it is a sync or refresh rate problem, but the fix is pretty easy.

---

