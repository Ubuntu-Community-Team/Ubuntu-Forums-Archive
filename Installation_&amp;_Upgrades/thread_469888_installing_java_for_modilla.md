---
title: "installing java for modilla"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by upintilldawn on 2007-06-10
i have been trying all day and night to get java to work on this system. i downloaded the newest ver of java from java did all steps. i installed java in /use/java did all links where the site told me to do it. yet it does not see the lnks what is it hat i am doing wrong. did install under super user. do i ned to chmod the link?

---

### Post by taurus on 2007-06-10
Do you see the new version on the list when you run this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by upintilldawn on 2007-06-10
> **taurus said:**
> Do you see the new version on the list when you run this command from a terminal?

```
sudo update-alternatives --config java
```



this is what i get when i ran that code.

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.


yet when i installed java it said it was installed.

java ver i install is 6 Update 1  both the Linux and Linux x64 did both installs as there web site told me

---

### Post by taurus on 2007-06-10
So you said you installed it to /usr/java.  What's the output of this command from a terminal?

```
ls -la /usr/java
```

---

### Post by upintilldawn on 2007-06-10
> **taurus said:**
> So you said you installed it to /usr/java.  What's the output of this command from a terminal?

```
ls -la /usr/java
```

total 12
drwxr-xr-x  3 root root 4096 2007-06-09 23:27 .
drwxr-xr-x 13 root root 4096 2007-06-09 21:41 ..
drwxr-xr-x  8 root root 4096 2007-06-09 23:27 jre1.6.0_01
lrwxrwxrwx  1 root root   42 2007-06-09 23:25 jre-6u1-linux-amd64.bin -> /home/paul/Desktop/jre-6u1-linux-amd64.bin
lrwxrwxrwx  1 root root   42 2007-06-09 23:22 jre.6u1-linux-amd64.bin -> /home/paul/Desktop/jre.6u1-linux-amd64.bin
lrwxrwxrwx  1 root root   41 2007-06-09 21:42 jre-6u1-linux-i586.bin -> /home/paul/Desktop/jre-6u1-linux-i586.bin


that is what i see.

lrwxrwxrwx  1 root root   42 2007-06-09 23:22 jre.6u1-linux-amd64.bin -> /home/paul/Desktop/jre.6u1-linux-amd64.bin
this is a mistake i did in making a link from where it was downloaded from to where i wanted to install it.

/usr/java/jre1.6.0_01 is the dir that it installed its self under the dir i installed it under.

---

### Post by upintilldawn on 2007-06-10
drwxr-xr-x  8 root root   4096 2007-06-09 23:27 .
drwxr-xr-x  3 root root   4096 2007-06-09 23:27 ..
drwxr-xr-x  2 root root   4096 2007-06-09 23:27 bin
-r--r--r--  1 root root   2487 2007-03-14 02:41 COPYRIGHT
drwxr-xr-x  2 root root   4096 2007-03-14 03:56 javaws
drwxr-xr-x 18 root root   4096 2007-06-09 23:27 lib
-r--r--r--  1 root root  11149 2007-03-14 02:41 LICENSE
drwxr-xr-x  4 root root   4096 2007-06-09 23:27 man
drwxr-xr-x  4 root root   4096 2007-03-14 03:56 plugin
-r--r--r--  1 root root  13998 2007-03-14 02:41 README
drwxr-xr-x  2 root root   4096 2007-06-09 21:45 .systemPrefs
-r--r--r--  1 root root 178596 2007-03-14 02:41 THIRDPARTYLICENSEREADME.txt
-r--r--r--  1 root root    968 2007-03-14 02:41 Welcome.html


is what i see if i do this command  ls -la /usr/java/jre1.6.0_01

---

### Post by taurus on 2007-06-10
```
sudo ln -s /usr/java/jre1.6.0_01/bin/java /usr/bin/java
java -version
```

---

### Post by upintilldawn on 2007-06-10
> **taurus said:**
> ```
sudo ln -s /usr/java/jre1.6.0_01/bin/java /usr/bin/java
java -version
```

laptop:~$ sudo ln -s /usr/java/jre1.6.0_01/bin/java /usr/bin/java java -version
ln: invalid option -- e
Try `ln --help' for more information

ok this is what i get. did i do it right?

---

### Post by taurus on 2007-06-10
> **upintilldawn said:**
> laptop:~$ sudo ln -s /usr/java/jre1.6.0_01/bin/java /usr/bin/java java -version
ln: invalid option -- e
Try `ln --help' for more information

ok this is what i get. did i do it right?

There are two separate commands.

```
sudo ln -s /usr/java/jre1.6.0_01/bin/java  /usr/bin/java [Return]
java -version [Return]
```

---

### Post by upintilldawn on 2007-06-10
if i do only java -version i get this

@laptop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

this is the ubuntu ver of java i installed first then uninstalled because it also did not work. the version i installed was 6.1

---

### Post by upintilldawn on 2007-06-10
> **taurus said:**
> There are two separate commands.

```
sudo ln -s /usr/java/jre1.6.0_01/bin/java  /usr/bin/java [Return]
java -version [Return]
```

@laptop:~$ sudo ln -s /usr/java/jre1.6.0_01/bin/java /usr/bin/java
ln: creating symbolic link `/usr/bin/java' to `/usr/java/jre1.6.0_01/bin/java': File exists

well that says my link is there so i did that right.

---

### Post by upintilldawn on 2007-06-10
does any one have any other ideas

---

### Post by Minosti on 2007-06-12
I had a similar situation with Java and Firefox.  In order to resolve it, I needed to create a symbolic link to the Java plugin in the Firefox/plugins folder.  However this was using OpenSUSE 10.2, but I have a feeling that the same thing will need to be done in this situation.

---

### Post by Slavomir on 2007-06-12
I've had similar problem. I've installed Ubuntu 6.06 and added newer wersion of Firefox 2 insted of system wersion 1.5. Java installed from repository in version 5 and 6  did'nt work in the browser. The problem was that old firefox was in /usr/lib/firefox and the plugin installed a symlink in to this location, But the new FF2 was installed by a script in to /opt/firefox dir. I've coppied the symlink from old location to the new ff location and java started to work without problems. If your situation is similar try this.

---

### Post by upintilldawn on 2007-06-18
ok i will try that ty

---

