---
title: "jre upgrade from jre 1.6.0 to 1.6.3 not working"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Mr.nano on 2008-02-02
hi all,

Here is my problem: I used jre 1.6.0 and download and installed 1.6.3 from sun website manually following the instructions given there. Everything went fine during the installation but, when I type
```
 sudo update-alternatives --config java 
```
the output is:
```
  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

```

```
java -version
```
the ouput is:
```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

No jre 1.6.3 presented there!
I installed the package jre-6u3-linux-i586.bin in the same directory where the other 2 are - /usr/lib/jvm/

```
ls -l /usr/lib/jvm/
```
the output is:
```
lrwxrwxrwx 1 root  root        23 2007-09-06 21:31 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.11
drwxr-xr-x 6 root  root      4096 2007-09-07 19:02 java-1.5.0-sun-1.5.0.11
lrwxrwxrwx 1 root  root        19 2007-09-10 16:44 java-6-sun -> java-6-sun-1.6.0.00
drwxr-xr-x 6 root  root      4096 2007-09-10 16:44 java-6-sun-1.6.0.00
drwxr-xr-x 8 root  root      4096 2008-02-02 15:42 jre1.6.0_03
-rwxr-xr-x 1 atapi atapi 19119599 2008-01-25 23:51 jre-6u3-linux-i586.bin
```
I dont remember why I put these link to the folder and should i put anothe one 4 the newly installed version o jre and what the name shuold be?

10X in advance for the help mates!

---

### Post by breakerr on 2008-03-19
> **Mr.nano said:**
> hi all,
[SIZE="1"]
Here is my problem: I used jre 1.6.0 and download and installed 1.6.3 from sun website manually following the instructions given there. Everything went fine during the installation but, when I type
```
 sudo update-alternatives --config java 
```
the output is:
```
  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

```

```
java -version
```
the ouput is:
```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

No jre 1.6.3 presented there!
I installed the package jre-6u3-linux-i586.bin in the same directory where the other 2 are - /usr/lib/jvm/

```
ls -l /usr/lib/jvm/
```
the output is:
```
lrwxrwxrwx 1 root  root        23 2007-09-06 21:31 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.11
drwxr-xr-x 6 root  root      4096 2007-09-07 19:02 java-1.5.0-sun-1.5.0.11
lrwxrwxrwx 1 root  root        19 2007-09-10 16:44 java-6-sun -> java-6-sun-1.6.0.00
drwxr-xr-x 6 root  root      4096 2007-09-10 16:44 java-6-sun-1.6.0.00
drwxr-xr-x 8 root  root      4096 2008-02-02 15:42 jre1.6.0_03
-rwxr-xr-x 1 atapi atapi 19119599 2008-01-25 23:51 jre-6u3-linux-i586.bin
```
I dont remember why I put these link to the folder and should i put anothe one 4 the newly installed version o jre and what the name shuold be?

10X in advance for the help mates[/SIZE]!

Hello there.....this is similar to my issue....but what happens to me is....

...I CANT UPDATE I have version 1.6.0_03 and I removed that to install version 1.6.0_05 but I don't get it.....trying and trying...avoiding to be bothering around here...but no clue...at the end I need your help guys, please!!!!!!!

I already tried this link from java sites but the part on the command to specify version I dont get it right chmod +x jdk-6<version>-linux-i586.bin What I'm suppose to change or how to edit/substitute the version part for....what goes in version with the arrows symbols or without it ??? and how could I know if I have permission like they mention there ( Make sure that execute permissions are set on the self-extracting binary.) ????

---

