---
title: "Matlab 2012a on 12.04 - installation crashes"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by Lenstrato on 2013-01-11
Hello,

I'm trying to install MatLab 2012a (32 bit) on Ubuntu 12.04. The furthest I get is this error message:
[INDENT]florian@FlorianOfficePC:~/Desktop/matlab_2011$ ./install -v
Preparing installation files ...
->  DVD                 = /home/florian/Desktop/matlab_2011
->  ARCH                = glnx86
->  DISPLAY             = :0
->  TESTONLY            = 0
->  JRE_LOC             = /tmp/mathworks_2691/sys/java/jre/glnx86/jre
->  LD_LIBRARY_PATH     = /home/florian/Desktop/matlab_2011/bin/glnx86
 
Command to run:
/tmp/mathworks_2691/sys/java/jre/glnx86/jre/bin/java  -splash:/home/florian/Desktop/matlab_2011/java/splash.png -Djava.ext.dirs=/tmp/mathworks_2691/sys/java/jre/glnx86/jre/lib/ext:/tmp/mathworks_2691/java/jar:/tmp/mathworks_2691/java/jarext:/tmp/mathworks_2691/java/jarext/axis2/:/tmp/mathworks_2691/java/jarext/guice/:/tmp/mathworks_2691/java/jarext/webservices/ com/mathworks/installwizard/Launcher -root "/home/florian/Desktop/matlab_2011" 
 
Installing ...
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (exceptions.cpp:364), pid=2716, tid=3062262592
#  Error: ExceptionMark destructor expects no pending exceptions
#
# JRE version: 6.0_17-b04
# Java VM: Java HotSpot(TM) Server VM (14.3-b01 mixed mode linux-x86 )
# An error report file with more information is saved as:
# /home/florian/Desktop/matlab_2011/hs_err_pid2716.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
Finished
[/INDENT]I already tried installing different versions of JRE, and pointing the installation towards them, but no succes. Does anyone have any tips on how to proceed?

Thanks in advance!

---

