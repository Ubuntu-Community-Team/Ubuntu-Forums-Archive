---
title: "Re: Any idea ???: LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS3)"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-12-11
I am suing abuntu 15.10
```
Test-Lenovo-Z50-75 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
and try to run opcua app
from here 
[http://www.openopcua.org/](http://www.openopcua.org/)

it app is zip and should be unzip.
then lunch it with an start.sh
inside start.sh
is 

```
export LD_LIBRARY_PATH=./:$LD_LIBRARY_PATH
./OpenOpcUaCoreServer ./ConfigOpenOpcUa.xml
```

************************************************************************************


when I run start,sh I get the following error

```
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
```

*********************************************************************************************************************************************************************'
```
ls -ld /usr/ /usr/lib/ /usr/lib/x86_64-linux-gnu/
ERROR: ld.so: object '/lib/i386-linux-gnu/libgcc_s.so.1' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
drwxr-xr-x  12 root root   4096 Nov  1 11:01 /usr/
drwxr-xr-x 193 root root  24576 Dec  9 18:08 /usr/lib/
drwxr-xr-x 126 root root 106496 Dec 10 18:11 /usr/lib/x86_64-linux-gnu/

```

***************************************************************************************************************************************************************************
When I use sudo I get the following output, witch seemed to be ok
```
sudo ls -ld /usr/ /usr/lib/ /usr/lib/x86_64-linux-gnu/
[sudo] password for test: 
drwxr-xr-x  12 root root   4096 Nov  1 11:01 /usr/
drwxr-xr-x 193 root root  24576 Dec  9 18:08 /usr/lib/
drwxr-xr-x 126 root root 106496 Dec 10 18:11 /usr/lib/x86_64-linux-gnu/
```

The app is a c++ application developed on windows but has a linux version

locate libgcc_s.so.1
/lib/i386-linux-gnu/libgcc_s.so.1
/lib/x86_64-linux-gnu/libgcc_s.so.1
/usr/lib32/libgcc_s.so.1
/usr/libx32/libgcc_s.so.1
***********************************************************
echo $LD_LIBRARY_PATH
./::/usr/lib64:/usr/lib/x86_64-linux-gnu

bump

Do I need to supply more info about my problem.. I am running out of googled options :)

---

### Post by steeldriver on 2015-12-12
The site you linked keeps timing out for me, however it looks like you're trying to run a 32-bit application on a 64-bit system without the necessary 32-bit library support

---

### Post by hoboy on 2015-12-12
> **steeldriver said:**
> The site you linked keeps timing out for me, however it looks like you're trying to run a 32-bit application on a 64-bit system without the necessary 32-bit library support
It seemed like you are right...
How can get the necessary 32-bit library ?

> **steeldriver said:**
> The site you linked keeps timing out for me, however it looks like you're trying to run a 32-bit application on a 64-bit system without the necessary 32-bit library support

It seemed like that the site is doing maintemances

---

### Post by hoboy on 2015-12-18
somebody please help.

---

### Post by ubfan1 on 2015-12-18
What's the value of LD_PRELOAD ?   You had to pay a fee, don't they offer any support?

---

