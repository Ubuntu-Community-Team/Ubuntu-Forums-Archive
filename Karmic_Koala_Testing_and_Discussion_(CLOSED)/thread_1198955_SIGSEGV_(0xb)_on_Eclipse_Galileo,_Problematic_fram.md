---
title: "SIGSEGV (0xb) on Eclipse Galileo, Problematic frame: # C [libgtk-x11-2.0.so.0+0xb5e59"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-06-28
Anyone else seeing this bug on eclipse galileo or other java apps?

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fa507d53e59, pid=13165, tid=140347587033424
#
# JRE version: 6.0-b16
# Java VM: OpenJDK 64-Bit Server VM (14.0-b15 mixed mode linux-amd64 )
# Distribution: Ubuntu karmic (development branch), package 6b16~pre3-0ubuntu1
# Problematic frame:
# C  [libgtk-x11-2.0.so.0+0xb5e59]
#
# An error report file with more information is saved as:
# /home/niall/Desktop/eclipse-cpp-galileo-linux-gtk-x86_64/hs_err_pid13165.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/393091](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/393091)

---

### Post by dinxter on 2009-06-28
seems to happen in vuze too if you can find a combo box to click such as,
tools->options->Connection->Proxy Options->SOCKS Version

so i'm guessing its a java wide bug rather than app specific

---

### Post by portis on 2009-06-28
It's a bug of gtk, see here:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/391398](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/391398)

You can downgrade your gtk library to 2.17.0.

---

### Post by dinxter on 2009-06-28
thanks, just noticed that it was across apps and jvm's so i'll mark it as duplicated of 391398

---

