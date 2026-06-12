---
title: "JAVA_HOME not giving error maven says not defined"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-10-22
/usr/lib/jvm/java-6-sun-1.6.0.20/bin
is the directory where my Java resides.
in the .bashrc have following
```

JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.20/bin"
export JAVA_HOME

```/etc/environment and /etc/profile
have the default entries no changes with them.
```

 echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.20/bin

```then Installed ```
aptitude install maven2
```when I run mvn get error
```

Error: JAVA_HOME is not defined correctly.
  We cannot execute /usr/lib/jvm/java-6-sun-1.6.0.20/bin/bin/java
```I am not having any clue as what is this error?
As to me JAVA_HOME seems to be defined.

Also worth mentioning
```

which java
/usr/bin/java
```

---

### Post by iansane on 2012-05-09
extremely old post I know but for the problem the OP had,

leave the "/bin" off when setting the home variable because Maven is appending "/bin/java" to the end of it on it's own.

However still getting the same "cannot execute" message.

It's permissions on the jdk directory. I installed mine in /opt (no special reason, just always putting manually installed things in opt)

So my path is "/opt/java/jdk1.7.0_04/bin/java"

So here's my java_home variable set in /etc/bash.bashrc
```

#java home 
JAVA_HOME=/opt/java/jre1.7.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME
export PATH

```

Then to get the message to go away I typed
```
sudo chmod -R 777 /opt/java/jdk1.7.0_04
```

Not going to leave it at 777 full open permissions but it shows that the issue Maven is having is it can't read or execute java because of permissions.

Just figured this out so hope it helps if someone else comes across this post.

---

