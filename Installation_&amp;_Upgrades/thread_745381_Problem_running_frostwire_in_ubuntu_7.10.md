---
title: "Problem running frostwire in ubuntu 7.10"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by los3rsluck on 2008-04-04
first off, im new to the whole linux world so sorry if anything is, well, you know, pretty obvious and whatnot... but when i first installed frostwire it all ran fine, but then i screwed something up and tried to fix it by following other threads, i ended up with a bunch of new java stuff and none of it worked, so i tried reinstalling frostwire, that didnt do much either, so now ive deleted all the java and reinstalled frostwire one last time, along with a fresh install of java6, i try to run frosywire from the terminal and get.. 

jordan@Jordan-Desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b849d62fe25, pid=22115, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid22115.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 22115 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

jordan@Jordan-Desktop:~$ 

... any help would be great

---

### Post by los3rsluck on 2008-04-04
nevermind everybody i just found the answer... only thing, in my apps>sound and video menu, the frostwire icon isnt the right icon, its just a blank window looking thing, any way to fix this? i can live with it because it works but ts kind of an ocd thing

---

