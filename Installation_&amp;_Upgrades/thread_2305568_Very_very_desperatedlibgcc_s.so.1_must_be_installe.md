---
title: "Very very desperated:libgcc_s.so.1 must be installed for pthread_cancel to work"
date: 2015-12-07
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-12-07
I m using ubuntu 15.04

and getting the errors bellow and master google is not helping:
OpenOpcUa:4143504000> Loading ./ ConfigOpenOpcUa.xml
OpenOpcUa:4143504000> Your XML configuration file : ./ConfigOpenOpcUa.xml has been parsed
OpenOpcUa:4143504000> ApplicationUri=urn:localhost:OpenOpcUa:4CEUAServer
OpenOpcUa:4143504000> Server listening at :
	opc.tcp://localhost:2564/4CEUAServer.
OpenOpcUa:4143504000> 1306 Nodes in the addressSpace split in 
	173 Objects 827 Variables 0 Views 34 Methods 
	96 ObjectTypes 26 ReferenceTypes 114 DataTypes 36 VariableTypes
OpenOpcUa:4143504000> Press Q or q to exit.
libgcc_s.so.1 must be installed for pthread_cancel to work
Aborted (core dumped)

---

### Post by steeldriver on 2015-12-07
What is OpenOpcUa? Where did you get it and how did you install it?

---

### Post by hoboy on 2015-12-07
[http://www.openopcua.org/](http://www.openopcua.org/)
 Thanks for asking

---

### Post by steeldriver on 2015-12-07
OK but that doesn't tell us exactly WHAT you installed or HOW - as far as I can see, the only Linux option is a Debian x86 binary. Is that what you used? Is your platform 32-bit or 64-bit?

---

### Post by hoboy on 2015-12-07
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid

uname -a
Linux test 3.19.0-39-generic #44-Ubuntu SMP Tue Dec 1 14:39:05 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


tks very much

Here are the libgcc_s.so.1  I get that when I use locate libgcc_s.so.1

/home/test/.local/share/Trash/files/libgcc_s.so.1
/home/test/.local/share/Trash/info/libgcc_s.so.1.trashinfo
/lib/i386-linux-gnu/libgcc_s.so.1
/lib/x86_64-linux-gnu/libgcc_s.so.1
/usr/lib/debug/lib/x86_64-linux-gnu/libgcc_s.so.1
/usr/lib/debug/usr/lib32/libgcc_s.so.1
/usr/lib/debug/usr/libx32/libgcc_s.so.1
/usr/lib32/libgcc_s.so.1
/usr/libx32/libgcc_s.so.1

Hello anybody ?

---

### Post by hoboy on 2015-12-07
Somebody please help

---

### Post by ian-weisser on 2015-12-07
You have answered only one of the four questions in Post #4.
Answering the others would help a lot.

---

