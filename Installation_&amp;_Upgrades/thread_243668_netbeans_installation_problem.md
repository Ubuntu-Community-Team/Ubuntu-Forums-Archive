---
title: "netbeans installation problem"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2006-08-25
i DL netbeans from their site and read this
[http://www.netbeans.org/community/releases/41/install.html](http://www.netbeans.org/community/releases/41/install.html)

i have install sun-1.5jdk,sdk everything from sun but all the time i get
A suitable JVM could not be found. Please run the installer again using the option -is:javahome <JAVA HOME DIR>

i try
 ./NetBeansIDE-release351-linux.bin -is:javahome /usr/lib/jvm/java-1.5.0-sun/
and
 ./NetBeansIDE-release351-linux.bin -is:javahome /usr/bin/java

but the same.
What i am doing wrong?

---

### Post by zxee on 2006-08-25
I really don't know for sure but check where jvm is on your system.
> which jvm Also check your path > echo $PATH Maybe you can use automatix to download java/jvm.
I know automatix will install java and that should mean the jvm.

---

### Post by mitjab on 2006-08-25
this is my echo $path
mitjab@ubuntu:~/Desktop$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
mitjab@ubuntu:~/Desktop$


which java is
/usr/bin/java which i already try but not working. I install java agin with automatrix but still not working.

java and javac works normally.

---

### Post by Stone123 on 2006-08-27
Is you need something in the path :
sudo echo "/some/path" >> /etc/ld.so.conf && sudo ldconfig

---

