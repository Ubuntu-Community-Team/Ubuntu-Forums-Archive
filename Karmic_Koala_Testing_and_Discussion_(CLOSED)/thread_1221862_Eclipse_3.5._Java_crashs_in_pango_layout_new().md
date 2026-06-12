---
title: "Eclipse 3.5. Java crashs in pango_layout_new()"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FarJumper on 2009-07-24
Eclipse have started to crash sometimes in karmic. I don't remember such behavior before. It become apparent in few places: when installing new plugin after pressing button "Finish" or while creating of new project.

Eclipse: 3.5.0 I20090611-1540
Ubuntu karmic current
Java: sun 1.6.0_14-b08

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x0054a596, pid=32643, tid=3087722176
#
# JRE version: 6.0_14-b08
# Java VM: Java HotSpot(TM) Client VM (14.0-b16 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libpango-1.0.so.0+0x23596]  pango_layout_new+0x36
#
# An error report file with more information is saved as:
# /home/vbuell/eclipse/hs_err_pid32643.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)

---

### Post by zergling_zzh on 2009-10-22
I got same issue here. Eclipse totally is not ready for karmic. I have to switch to netbeans :(

---

### Post by lean on 2009-10-22
export GDK_NATIVE_WINDOWS=true
./eclipse

Could be a fix, dunno.

---

### Post by siml on 2009-10-25
Same problem... very annoying! The  posted workarround isn't working.. Many people have this problem, search google with "pango_layout_new+0x36".

ng

---

### Post by nthykier on 2009-10-28
Hi

It sounds like you are suffering from bug #460104[1]. 

~Niels 

[1] [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/460104](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/460104)

---

