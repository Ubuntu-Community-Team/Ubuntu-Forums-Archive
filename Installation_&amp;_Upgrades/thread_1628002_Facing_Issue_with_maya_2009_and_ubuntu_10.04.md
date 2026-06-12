---
title: "Facing Issue with maya 2009 and ubuntu 10.04"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by Achayaan on 2010-11-22
Hi All,

After upgrading to ubuntu 10.04 , I am unable to open maya its suddenly crashing 
here is the crash log
[PHP]
                       GNU gdb (GDB) 7.1-ubuntu
                      Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
                      For bug reporting instructions, please see:
                      <http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/autodesk/maya2009-x64/bin/maya.bin...(no debugging symbols found)...done.
                      (gdb) r
                      Starting program: /usr/autodesk/maya2009-x64/bin/maya.bin 
                      [Thread debugging using libthread_db enabled]
                      [New Thread 0x7fffe96b3710 (LWP 3667)]
                      [New Thread 0x7fffe92b2710 (LWP 3668)]
                      MAYA_DEBUG_NO_SIGNAL_HANDLERS is set.
                      
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff4108497 in TinputDeviceManager::deviceByIndex(short) const ()
                         from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
(gdb) bt
#0  0x00007ffff4108497 in TinputDeviceManager::deviceByIndex(short) const ()
                         from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#1  0x00007ffff40c5766 in Twindow::unStow(Tevent const&) () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
                       #2  0x00007ffff40c6f54 in TstartupWnd::unStow(Tevent const&) ()
                         from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#3  0x0000000000414f8d in TmayaApp::initPreGUI() ()
                      #4  0x0000000000412f22 in TmayaApp::create() ()
                      #5  0x00000000004105ea in appmain() ()
                      #6  0x000000000041e99b in main ()
(gdb)                     
[/PHP]

So i got this info from autodesk forum

```
When Maya 2009 was released, the Linux distros were not using XInput 2.0  packages. Maya was not expecting the version change, and gets into a  partial initialization state
```

Any one is there any possible way that I can disable XInput or I can solve this issue ?

thanks in advance

---

### Post by Achayaan on 2010-11-24
Bumppppppp any help ? :(

---

### Post by Achayaan on 2010-11-26
Please some can help me :(

---

### Post by Achayaan on 2010-11-29
Please help me :(

---

### Post by Achayaan on 2010-12-13
Why I am not getting any reply :(

---

### Post by azmand01 on 2011-01-12
I have the same problem. Searched all oer and can not find a solution.

---

### Post by Achayaan on 2011-02-19
any one can give any help .. please ?

---

