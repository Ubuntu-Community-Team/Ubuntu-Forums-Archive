---
title: "Change the Java path"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by shujamughal on 2010-06-05
Hi
I have the ubuntu 10. and install the sun java manually and copy the folder in usr/lib/jvm/java-6-sun.

Now when i run this command 

 **sudo update-java-alternatives -s java-6-sun**

then i get the following message.

**file does not exist: /usr/lib/jvm/.java-6-sun.jinfo**


I have also update the etc/bash.bashrc file and in the end of file. write these lines

.....
fi
[B]JAVA_HOME=/usr/lib/jvm/java-6-sun
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH[/B]

Also i have updated this file etc/environment and add the following lines.

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
[B]LANG="en_AU.UTF-8"
LANGUAGE="en_AU:en"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
CLASSPATH="/usr/lib/jvm/java-6-sun/lib:."[/B]


BUT The java -version command gives this output.

[B]root@digitalvision:~# java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)[/B]

I want to set sun java but despite of my all efforts, it still refer to openjdk.

Kindly help me out.

Regards
Shuja

---

