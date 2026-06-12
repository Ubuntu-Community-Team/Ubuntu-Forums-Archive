---
title: "Broken softlink"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by prc320 on 2007-01-25
Hi

I have a problem Installing Java 1.6.0. I get almost to the end when the command goes like this:

root@Powerc:/home/symsr# cd /home/symsr/.mozilla/plugins
[email]root@Powerc:/home/symsr/.mozi[/email]lla/plugins# ln -s /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

This looks ok but when I go graphical it is "broken"

What do I do?

Robert

---

### Post by taurus on 2007-01-25
Why don't you just log in to your regular account, symsr, and run

```
ln -s /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so   ~/.mozilla/plugins
```

---

### Post by prc320 on 2007-01-25
It is still broken!

---

### Post by taurus on 2007-01-25
What do you mean broken?  What's the output of these two commands from a terminal?

```
ls -la ~/.mozilla/plugins
ls -la /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7
```

---

### Post by prc320 on 2007-01-25
> **prc320 said:**
> It is still broken!


symsr@Powerc:~$ ls -la ~/.mozilla/plugins
total 2136
drwxr-xr-x 2 symsr symsr    4096 2007-01-25 15:12 .
drwx------ 4 symsr symsr    4096 2007-01-11 16:00 ..
-rw-r--r-- 1 symsr symsr    6148 2006-08-07 16:21 .DS_Store
-rw-r--r-- 1 symsr symsr     856 2006-07-26 17:11 flashplayer.xpt
-rwxr-xr-x 1 symsr symsr 2154768 2006-07-26 17:11 libflashplayer.so
lrwxrwxrwx 1 root  root       68 2007-01-25 15:12 libjavaplugin_oji.so -> /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

and

symsr@Powerc:~$ ls -la /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7
ls: /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7: No such file or directory
symsr@Powerc:~$ 

I don't see the last one!

Robert

---

### Post by taurus on 2007-01-25
> **prc320 said:**
> 
symsr@Powerc:~$ ls -la /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7
ls: /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7: No such file or directory
symsr@Powerc:~$ 

Robert

That's your problem there.  Apparently, you don't have /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7!  so, your java plugin is not in there then.  What about

```
/usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386
```

---

### Post by prc320 on 2007-01-26
symsr@Powerc:~$ cd /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386
bash: cd: /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386: No such file or directory
symsr@Powerc:~$ 

Again no file or directory!

Robert

---

### Post by taurus on 2007-01-26
```
cd /usr/lib/jvm/java-1.6.0-sun/jre
```

---

### Post by prc320 on 2007-01-26
This is only goes as like:

*/usr/lib..*.  this is nothing for *jvm* at all!

---

### Post by taurus on 2007-01-26
Then, where did you install java 1.6?  What happens when you run this command from a terminal?

```
whereis java
-or-
sudo find / -name java -print
```

---

### Post by prc320 on 2007-01-27
I have the following:

symsr@Powerc:~$ whereis java
java: /usr/bin/java /usr/X11R6/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz
symsr@Powerc:~$ sudo find / -name java -print
Password:
/var/lib/dpkg/alternatives/java
/etc/alternatives/java
/usr/bin/java
/usr/lib/openoffice/share/Scripts/java
/usr/share/java
/usr/java
/usr/java/jdk1.6.0/jre/bin/java
/usr/java/jdk1.6.0/bin/java
/usr/java/jre1.6.0/bin/java
/usr/java/jre1.5.0_10/bin/java
symsr@Powerc:~$ 

Robert

---

### Post by taurus on 2007-01-27
So your Sun's java is in /usr/java/jdk1.6.0/bin/java, not /usr/lib/jvm/java-1.6.0-sun/bin/java.  Therefore, what's the output of these two commands?

```
/usr/java/jdk1.6.0/bin/java -version
ls -la /usr/java/jdk1.6.0/
```

---

### Post by prc320 on 2007-01-29
This is the output:

symsr@Powerc:~$ /usr/java/jdk1.6.0/bin/java-version
bash: /usr/java/jdk1.6.0/bin/java-version: No such file or directory
symsr@Powerc:~$ ls -la /usr/java/jdk1.6.0/
total 18540
drwxr-xr-x 10 symsr symsr     4096 2006-11-29 11:25 .
drwxr-xr-x  5 root  root      4096 2007-01-24 17:10 ..
drwxr-xr-x  2 symsr symsr     4096 2006-11-29 11:25 bin
-r--r--r--  1 symsr symsr     2487 2006-11-29 09:49 COPYRIGHT
drwxr-xr-x  5 symsr symsr     4096 2006-11-29 11:25 db
drwxr-xr-x 10 symsr symsr     4096 2006-11-29 11:25 demo
drwxr-xr-x  3 symsr symsr     4096 2006-11-29 11:25 include
drwxr-xr-x  7 symsr symsr     4096 2007-01-24 14:00 jre
drwxr-xr-x  2 symsr symsr     4096 2007-01-24 14:00 lib
-r--r--r--  1 symsr symsr    13198 2006-11-29 09:49 LICENSE
drwxr-xr-x  4 symsr symsr     4096 2006-11-29 11:25 man
-r--r--r--  1 symsr symsr    25379 2006-11-29 09:49 README.html
-r--r--r--  1 symsr symsr    20320 2006-11-29 09:49 README_ja.html
-r--r--r--  1 symsr symsr    15160 2006-11-29 09:49 README_zh_CN.html
drwxr-xr-x  9 symsr symsr     4096 2006-11-29 11:25 sample
-rw-r--r--  1 symsr symsr 18652677 2006-11-29 09:49 src.zip
-r--r--r--  1 symsr symsr   175919 2006-11-29 09:49 THIRDPARTYLICENSEREADME.txt
symsr@Powerc:~$

---

### Post by taurus on 2007-01-29
```
ls -la /usr/java/jdk1.6.0/jre/plugins
```

p.s.  There should be a space betwee **java** and **-version**.

```
/usr/java/jdk1.6.0/bin/java -version
```

---

### Post by prc320 on 2007-01-29
This is output now!

symsr@Powerc:~$ ls -la /usr/java/jdk1.6.0/jre/plugins
ls: /usr/java/jdk1.6.0/jre/plugins: No such file or directory
symsr@Powerc:~$ /usr/java/jdk1.6.0/bin/java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
symsr@Powerc:~$

---

### Post by taurus on 2007-01-29
```
ls -la /usr/java/jdk1.6.0/jre
```

---

### Post by prc320 on 2007-01-29
symsr@Powerc:~$ ls -la /usr/java/jdk1.6.0/jre
total 240
drwxr-xr-x  7 symsr symsr   4096 2007-01-24 14:00 .
drwxr-xr-x 10 symsr symsr   4096 2006-11-29 11:25 ..
drwxr-xr-x  2 symsr symsr   4096 2006-11-29 11:25 bin
-r--r--r--  1 symsr symsr   2487 2006-11-29 09:47 COPYRIGHT
drwxr-xr-x  2 symsr symsr   4096 2006-11-29 11:25 javaws
drwxr-xr-x 17 symsr symsr   4096 2007-01-24 14:00 lib
-r--r--r--  1 symsr symsr  11149 2006-11-29 09:47 LICENSE
drwxr-xr-x  4 symsr symsr   4096 2006-11-29 11:25 plugin
-r--r--r--  1 symsr symsr  14007 2006-11-29 09:47 README
drwxr-xr-x  2 symsr symsr   4096 2007-01-24 14:00 .systemPrefs
-r--r--r--  1 symsr symsr 175919 2006-11-29 09:47 THIRDPARTYLICENSEREADME.txt
-r--r--r--  1 symsr symsr    968 2006-11-29 09:47 Welcome.html
symsr@Powerc:~$ 


Robert

---

### Post by taurus on 2007-01-29
D'OH!  I had an extra **s** at the end.

```
s -la /usr/java/jdk1.6.0/jre/plugin
```

---

### Post by prc320 on 2007-01-29
symsr@Powerc:~$ ls -la /usr/java/jdk1.6.0/jre/plugin
total 16
drwxr-xr-x 4 symsr symsr 4096 2006-11-29 11:25 .
drwxr-xr-x 7 symsr symsr 4096 2007-01-24 14:00 ..
drwxr-xr-x 2 symsr symsr 4096 2006-11-29 11:25 desktop
drwxr-xr-x 4 symsr symsr 4096 2006-11-29 11:25 i386
symsr@Powerc:~$

---

