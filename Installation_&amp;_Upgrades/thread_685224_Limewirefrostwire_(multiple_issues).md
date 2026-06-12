---
title: "Limewire/frostwire (multiple issues)"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by einherier on 2008-02-02
Opps, i just noticed I put this in the wrong forum.. sorry


I installed frostwire and tried to get it to work but i get the following error message:

```

pra3torian@pra3torian:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b78d4f7ce25, pid=11932, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid11932.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 11932 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

```


```
pra3torian@pra3torian:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

```


I have looked for the "hs_err_pid11932.log" file but I cant find the damned thing anywhere.


I am running limewire but it acts weird, It wont close when i try to close it, and it doesn't save my settings when i close out.

I tried to uninstall these 2 programs, so that i could maybe reinstall them, but neither one appear in my Add/Remove thingy.

I tried to go into the synaptic package manager, but I simply can NOT find it anywhere.

Sorry guys, I know im beating this forum up, but I am doing the best i can.

---

### Post by VvWolverinevV on 2008-02-03
The jre packages you need are:

sun-java6-jre
sun-java6-bin

but it looks like you already have the latest approved version installed.  Are you sure that LimeWire isn't saving your settings?  I get the first-run wizard every time I run LimeWire, but it *does* save my settings on exit.

---

### Post by einherier on 2008-02-06
> **VvWolverinevV said:**
> The jre packages you need are:

sun-java6-jre
sun-java6-bin

but it looks like you already have the latest approved version installed.  Are you sure that LimeWire isn't saving your settings?  I get the first-run wizard every time I run LimeWire, but it *does* save my settings on exit.

You are correct, it is saving my settings....


I still can not get frostwire to work after installing thouse two packages from synaptic....do i need to take further action under the console or somethinG?


thanks

---

