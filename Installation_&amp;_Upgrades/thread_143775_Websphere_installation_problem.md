---
title: "Websphere installation problem"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by bushan on 2006-03-13
Hi, 
I am trying to install IBM Websphere community Edition on my ubuntu linux.
I have strange problem with the SUN JRE 

Please look at the log file below:
my 



Log file created by MultiPlatform installer @Mon Mar 13 03:54:47 CST 2006
INSTALLER_PATH=/home/nagabushan/Desktop/websphere/./setup-wasce.bin
running inner launcher=/tmp/istemp21846072035447/setup-wasce.bin.embedded -is:orig /home/nagabushan/Desktop/websphere/. -is:$Log file created by MultiPlatform installer @Mon Mar 13 03:54:48 CST 2006
INSTALLER_PATH=/tmp/istemp21846072035447/setup-wasce.bin.embedded
Checking the environment variables specifed in the JVM files to find the JVM...
Verifying... /usr/bin/java  -cp  /tmp/istemp21846072035448/Verify.jar Verify  java.vendor java.version
$JAVA_HOME is not defined in the shell environment specifed in the JVM FILE ibmjre142.jvm
$JAVAHOME is not defined in the shell environment specifed in the JVM FILE ibmjre142.jvm
$JDK_HOME is not defined in the shell environment specifed in the JVM FILE ibmjre142.jvm
Verifying... /usr/bin/java -cp /tmp/istemp21846072035448/Verify.jar Verify  java.vendor java.version
$JAVA_HOME is not defined in the shell environment specifed in the JVM FILE sunjre142.jvm
$JAVAHOME is not defined in the shell environment specifed in the JVM FILE sunjre142.jvm
$JDK_HOME is not defined in the shell environment specifed in the JVM FILE sunjre142.jvm
No JVM can  be found using the shell environment variable. Searching JVM will continue with Path Hints specified in the JVM $--------------------------------------------------------------------------------------------
Searching a JVM using /tmp/istemp21846072035448/ibmjre142.jvm
Verifying... **/opt/jdk1.5.0_06/bin/java**  -cp  /tmp/istemp21846072035448/Verify.jar Verify  java.vendor java.version
Verification failed for /opt/jdk1.5.0_06/bin/java using the JVM file /tmp/istemp21846072035448/ibmjre142.jvm.
--------------------------------------------------------------------------------------------
Searching a JVM using /tmp/istemp21846072035448/sunjre142.jvm
Verifying... **/opt/jdk1.5.0_06/bin/java** -cp /tmp/istemp21846072035448/Verify.jar Verify  java.vendor java.version
Verification failed for /opt/jdk1.5.0_06/bin/java using the JVM file /tmp/istemp21846072035448/sunjre142.jvm.




my JAVA is at location /opt/jdk1.5.0_06/bin/java
please help  me installing webspere. Atleast we can make a ubuntu wiki
I tried installing websphere with other linux distro.It worked good

Thanks

---

### Post by mururoa on 2006-03-13
Maybe it needs java 1.4.2 ?
Check java version on other distros where it works.

---

