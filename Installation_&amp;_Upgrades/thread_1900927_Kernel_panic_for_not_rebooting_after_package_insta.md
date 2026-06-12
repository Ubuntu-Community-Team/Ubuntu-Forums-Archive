---
title: "Kernel panic for not rebooting after package installations"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2011-12-27
This has been, at least, my fourth reinstalling of 11.10 from a USB to my Acer netbook.

And, it appears that when I download and install packages, and then do a reboot, then there is no problem - the system will boot from having been shutdown.

If I fail to run a reboot after installing new packages, the system will not boot from shutdown. I do not think it is the package that is causing it, because the package installed has been different at each instance prior to the kernel panic.

I don't know if it can be solved with doing a system check, because I cannot get into the kernel menu.

Any ideas, because it gets difficult to remember to reboot.

---

### Post by sidewalkcynic on 2011-12-27
Well, I guess I found a bug report, but there does not seem to be a fix as of yet.

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (sharedRuntime.cpp:762), pid=1783, tid=3010771824
#  guarantee(cb->is_adapter_blob() || cb->is_method_handles_adapter_blob()) failed: exception happened outside interpreter, nmethods and vtable stubs (1)
#
# JRE version: 6.0_23-b23
# Java VM: OpenJDK Client VM (20.0-b11 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.11pre
# Distribution: Ubuntu 11.10, package 6b23~pre11-0ubuntu1.11.10
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#

---------------  T H R E A D  ---------------

Current thread (0xb4988400):  JavaThread "AWT-EventQueue-0" [_thread_in_Java, id=1803, stack(0xb36fb000,0xb374c000)]

Stack: [0xb36fb000,0xb374c000]
```

---

