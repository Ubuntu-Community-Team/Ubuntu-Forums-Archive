---
title: "Set Path on /etc/environment"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by rathna on 2012-03-11
I installed java from Oracle. As per [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables), set the PATH at /etc/environment.
```
$sudo vi /etc/environment
JAVA_HOME="/usr/local/jdk1_6"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:$JAVA_HOME/bin"
```

I logged out and restarted the host just to be sure.

Now when I try running ./startup.sh from Tomcat,
$sudo ./startup.sh
```
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
```

However, when I try the following, it works:
```
$ $JAVA_HOME/bin/javac -version
javac 1.6.0_31
```

But the following command is unable to find the right path,
```
$ javac -version
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>
```

I probably could just throw it in the /etc/profile and I'm sure it'll work. But Ubuntu recommends /etc/environment! Could any of you help me fix the issue using /etc/environment?

Thank you.

---

### Post by lrgmmc on 2012-03-11
have you ran ```
sudo update-alternatives --config java
```? if not give it a try.Maybe helpful.

---

### Post by rathna on 2012-03-12
Hi, I don't think update-alternatives will address the problem since I don't want to create symbolic links within the bin directories. My question is how to get it working as per Ubuntu's recommendation by using /etc/environment.

Anyhow I tried your suggestion and I got this:

```
update-alternatives: error: no alternatives for java.
```

Thank you.

---

### Post by rathna on 2012-03-12
Found it!

since /etc/environment is a plain text file and not a shell script, $JAVA_HOME will not be recognized.

Therefore, including the entire path in the PATH variable worked wonderfully.

The following is my working /etc/environment file
```
$cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/jdk1_6/bin"
```

---

