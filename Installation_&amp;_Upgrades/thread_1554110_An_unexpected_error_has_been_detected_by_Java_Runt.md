---
title: "An unexpected error has been detected by Java Runtime Environment:"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by sukumarreddy on 2010-08-16
Hi friends,

Today i had installed COMSOL in ubuntu 10.04 in my dell studio laptop.
After successful installation following error was occurred.
Can any body help me to solve this problem.
(Note Matlab 2009b with 64bit working very fine).

```

$ sh comsol
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fc0c22ea390, pid=17495, tid=140466991306496
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (11.3-b02 mixed mode linux-amd64)
# Problematic frame:
# C  [libGL.so.1+0x30390]  glXGetConfig+0x40
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid17495.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted

```

---

### Post by fetapia on 2010-12-06
I'v the same issue.

Wich version of COMSOL have you installed?

I've tried with the 4.0 one. I think i'll try with the 4.0a, because i hadn't that problem with the 3.5a version

---

