---
title: "mercury messenger tray icon"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by gotjam on 2007-05-16
i installed mercury messenger 1.8, and when i disable the tray icon, all perfect.

when i enable it i recibe this error:

```
16:10:54:792 [20%]   Loading tray icon...
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x8fcb62ce, pid=9341, tid=3084192656
#
# Java VM: Java HotSpot(TM) Server VM (1.6.0_01-b06 mixed mode)
# Problematic frame:
# C  [libXt.so.6+0x162ce]  _XtAppCreateShell+0x5e
#
# An error report file with more information is saved as hs_err_pid9341.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/bin/mercury: line 16:  9341 Cancelado               (core dumped) java -Djava.library.path=jni/linux:jni/linux/jmf -classpath $classpath com.dMSN.Main

```

how do i fix it?

thanks

---

