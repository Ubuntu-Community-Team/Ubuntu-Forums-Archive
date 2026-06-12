---
title: "Java crashes in 14.10"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2015-04-23
I have been using Ubuntu since 2006 (8.04) and have never had so many serious problems as I am experiencing with 14.10. I am spending days trying to get applications and programs that worked seamlessly in 14.04 to work in 14.10 and I am seriously thinking of deleting the partition and re-installing 14.04. Or maybe it is time to change distros.

The latest problem to show up is a Java runtime problem. I use the Arduino IDE and if I try and save a sketch the IDE crashes with the following messages. I have tried different JRE's such as oracle-java7, oracle-java8 and icedtea but it always crashes and doesn't save the sketch.

```
~$ arduino
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f26f320a70c, pid=6714, tid=139804138272512
#
# JRE version: Java(TM) SE Runtime Environment (8.0_45-b14) (build 1.8.0_45-b14)
# Java VM: Java HotSpot(TM) 64-Bit Server VM (25.45-b02 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libawt_xawt.so+0x4470c]  handle_response+0xac
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid6714.log
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
#
/usr/bin/arduino: Zeile 36:  6714 Abgebrochen             (Speicherabzug geschrieben) java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel processing.app.Base "$@"
```

Does anyone know what is wrong?

---

### Post by sgian on 2015-04-25
Have you tried purging Oracle Java and then installing openJDK?  I know sometimes Oracle Java works better for some applications, but perhaps this application might work better with openJDK?

Since you are having problems with 14.10 compared to 14.04, I can think of two possible reasons...one is that the installation got corrupted and the other is that the newer kernel doesn't support your hardware as well.  If the installation got corrupted, a fresh installation might help.  But if you have an old amd-based computer you might be stuck with older versions of any form of linux.

---

