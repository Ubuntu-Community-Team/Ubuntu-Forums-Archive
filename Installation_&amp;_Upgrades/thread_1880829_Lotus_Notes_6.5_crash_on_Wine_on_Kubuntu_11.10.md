---
title: "Lotus Notes 6.5 crash on Wine on Kubuntu 11.10"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Anquietas on 2011-11-14
Hello,

I have a very strange problem.

I've upgraded from Ubuntu 11.04 to Kubuntu 11.10 (yes, the KDE Version).

I've installed Wine and then Lotus Notes 6.5.

The problem is that almost everytime when I exit Lotus Notes, it seems to crash. 
A window appears telling me that "NSD is Running !"... and an error-like window.

A log file is generated in my ~/.wine/drive_c/lotus/notes/data/IBM_TECHNICAL_SUPPORT/nsd_all_W32I_amgpc_11_14@17_48.log

When I examine this log it says a lot of stuff, and is ending with the following:

> 
Active Users:
 UID     Name 


   INFO  PID PPID   UID     STIME    COMMAND
        000e 000a     0 11/14 17:47:20 [services:000e]
        0011 000e     0 11/14 17:47:20   [ntoskrnl:0011]
        0017 000e     0 11/14 17:47:20   [plugplay:0017]
        001d 000c     0 11/14 17:47:20 [explorer:001d]
     -> 0021 001f     0 11/14 17:47:21 [ nlnotes:0021]
     -> 002c 0021     0 11/14 17:47:50   [ntaskldr:002c]
        002f 0021     0 11/14 17:48:33   [     nsd:002f]
        0031 002f     0 11/14 17:48:33     [wineconsole:0031]
INFO (0): Starting Debugger
** Attach to [ nlnotes:0021]
ERROR (0): StackWalk failed - (998) No access to memory location


Almost everytime I run Lotus Notes 6.5 emulated on Wine.

My OS is Kubuntu 11.10, and my Wine version is 1.3.28

It seems a New problem, because everytime I ran Lotus Notes on older versions of Ubuntu (GNOME), it worked very well...

Please help me.

---

### Post by Mark Phelps on 2011-11-14
Lotus Notes v6.5 has a "silver" rating on the WineHQ site -- which means it works, but has problems.

See the details in the link below.  Maybe some of the testing results will provide fixes that help you:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=27]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=27")

---

