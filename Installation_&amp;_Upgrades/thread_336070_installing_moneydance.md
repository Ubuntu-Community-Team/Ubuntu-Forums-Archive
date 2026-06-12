---
title: "installing moneydance"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by rbhigday on 2007-01-11
I am trying to install moneydance, this is what I did. ```
rbhigday@richard-laptop:~/downloads$ ./moneydance_linux_x86wj.sh
bash: ./moneydance_linux_x86wj.sh: Permission denied
rbhigday@richard-laptop:~/downloads$ sudo ./moneydance_linux_x86wj.sh
Password:
sudo: ./moneydance_linux_x86wj.sh: command not found
rbhigday@richard-laptop:~/downloads$ 

```

what did I do wrong?

---

### Post by PilotJLR on 2007-01-11
It may not be executable as root... try to do a "sudo chmod a+x <moneydance...>" on it before you run it as sudo.
If that doesn't work, then pls post the output of an "ls -l"

---

### Post by rbhigday on 2007-01-11
> **PilotJLR said:**
> It may not be executable as root... try to do a "sudo chmod a+x <moneydance...>" on it before you run it as sudo.
If that doesn't work, then pls post the output of an "ls -l"

Thanks this is what I got during installation. ```
rbhigday@richard-laptop:~/downloads$ sudo ./moneydance_linux_x86wj.sh
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
/usr/share/themes/Crux/gtk-2.0/gtkrc:77: Engine "crux-engine" is unsupported, ignoring
/usr/share/themes/Crux/gtk-2.0/gtkrc:110: Engine "crux-engine" is unsupported, ignoring

```

are the things ignored critical or is there something I need to install or update?

---

### Post by rbhigday on 2007-01-12
Thanks for the help. As you can see [COLOR="Navy"][here]("http://www.ubuntuforums.org/showthread.php?t=336840")[/COLOR] I was successful.

---

### Post by rbhigday on 2007-01-15
ok now that the desktop boots to ubuntu I am trying to install moneydance there to use instead of the laptop. I get an error

```
Error: no `server' JVM at `/home/richard/downloads/moneydance_linux_x86wj.sh.16841.dir/jre/lib/i386/server/libjvm.so'.

```

any ideas what I need to do, and just use the laptop is not a preferred solution :P

---

### Post by taurus on 2007-01-15
Do you have a java on your desktop?

```
java -version
```

---

### Post by rbhigday on 2007-01-15
> **taurus said:**
> Do you have a java on your desktop?

```
java -version
```

```
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
richard@richard-desktop:~$ 


```

---

### Post by taurus on 2007-01-15
You need to install Sun's java, the actual java, on your desktop though.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by rbhigday on 2007-01-15
> **taurus said:**
> You need to install Sun's java, the actual java, on your desktop though.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

ok dumb question 52342342798798273984729875982734987239487293.4

did i install the right one?

```
richard@richard-desktop:~/downloads$ java -version
java version "1.5.0_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_10-b03)
Java HotSpot(TM) Server VM (build 1.5.0_10-b03, mixed mode)


```

---

### Post by taurus on 2007-01-15
That's the right now.  Now, see if you can install your moneydance again.

---

### Post by rbhigday on 2007-01-15
Nope did not work.

Then i went to the moneydance site and found this coomand
```

export INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.10
```

then I did this
```

sudo chmod a+x moneydance_linux_x86.sh
sudo ./moneydance_linux_x86.sh

```

Now I will mail the data file to me and I will be done :)

Thanks again

---

### Post by jwillar on 2007-06-18
I have been following this discussion closely because I am having the same problem trying to get 'moneydance' installed.  So far It has only danced out of my reach.  Here are my results of my latest attempt

===================
john@DELL03:~/Moneydance$ sudo chmod a+x moneydance_linux_x86wj.sh
john@DELL03:~/Moneydance$ sudo ./moneydance_linux_x86wj.sh
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Error: no `server' JVM at `/home/john/Moneydance/moneydance_linux_x86wj.sh.13112 .dir/jre/lib/i386/server/libjvm.so'.
john@DELL03:~/Moneydance$
===================

So why is this so hard?

---

### Post by jwillar on 2007-06-18
I finally got Moneydance to install and run. It turns out the latest Java files were already loaded (Kubuntu 7.4) so I just needed to download the copy w/o java. My next problem was failing to run the scripts provided above in the same directory as the downloaded file.

Thanks for the help.

---

