---
title: "JAVA_HOME not defined"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-08-01
My OS Ubuntu 9.04

I installed java via 
```

apt-get install sun-java6-jre 
```also I downloaded ant-1.8.1 binary
from [here]("http://ant.apache.org/bindownload.cgi")
unpacked in 

in /usr/lib/apache-ant-1.8.1/
Created  /etc/profile.d/ant.sh 
and /etc/profile.d/jdk.sh

contents of
/etc/profile.d/ant.sh are
```

export ANT_HOME=/usr/lib/apache-ant-1.8.1
export PATH=$ANT_HOME/bin:$PATH

```and  /etc/profile.d/jdk.sh
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun/bin
export PATH=$JAVA_HOME/bin:$PATH


```Now logged out and logged in again in my system checked
```

echo $ANT_HOME
/usr/lib/apache-ant-1.8.1

```and 
```

root@tapas-laptop:~# echo $JAVA_HOME
/usr/lib/jvm/java-6-sun/bin

```After which I type on command prompt 
```
ant
``` and get the following error
```

Error: JAVA_HOME is not defined correctly.   We cannot execute /usr/lib/jvm/java-6-sun/bin/bin/java
```both the file ant.sh and jdk.sh are executable
Searched this on [net ]("http://www.google.co.in/search?q=Error%3A+JAVA_HOME+is+not+defined+correctly.+++We+cannot+execute+%2Fusr%2Flib%2Fjvm%2Fjava-6-sun%2Fbin%2Fbin%2Fjava&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")
Nothing useful seems to come across.

---

### Post by tapas_mishra on 2010-08-01
> **tapas_mishra said:**
> My OS Ubuntu 9.04

[/code]and  /etc/profile.d/jdk.sh
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun/bin
export PATH=$JAVA_HOME/bin:$PATH

```
I got my mistake had incorrectly set JAVA_HOME to point to bin 
changing ```
JAVA_HOME=/usr/lib/jvm/java-6-sun/bin
```
to 
```
JAVA_HOME=/usr/lib/jvm/java-6-sun 
```
I had added bin at the last in above.

---

