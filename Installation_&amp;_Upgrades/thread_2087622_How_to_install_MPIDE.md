---
title: "How to install MPIDE"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by kaloasd on 2012-11-24
I have the necessary libs, I downloaded the IDE and unzipped  it. I added the```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jni
```
to the end of the file.
I followed the instructions here
[http://www.chipkit.org/wiki/index.php?title=MPIDE_Installation](http://www.chipkit.org/wiki/index.php?title=MPIDE_Installation)
 Now I have no idea what to do.

---

### Post by kaloasd on 2012-11-28
Can anyone tell me which file do I click to start it

---

### Post by Abhinav Kumar on 2012-11-28
> **kaloasd said:**
> Can anyone tell me which file do I click to start it
Hi kaloasd,
I think there should be some executable/binary file in that directory. They can be executed by opening a terminal and then going to the folder.

```

cd /PATH/TO/FOLDER

```

Then execute it by saying 
```

./FILE

```
Here, FILE should be replaced with that executable or bin file.
Make sure you have proper permissions to execute this file.

Regards,
Abhinav

---

### Post by kaloasd on 2012-11-28
Thank you for replying. 

I found a make.sh and after some fiddling managed to start something. It asks for a folder to put the sketches in and then gives me this
```
Exception in thread "main" java.lang.NullPointerException
    at processing.app.Base.getTarget(Base.java:1624)
    at processing.app.Base.getBoardPreferences(Base.java:1662)
    at processing.app.Base.<init>(Base.java:271)
    at processing.app.Base.main(Base.java:183)

```

---

### Post by Abhinav Kumar on 2012-11-29
> **kaloasd said:**
> Thank you for replying. 

I found a make.sh and after some fiddling managed to start something. It asks for a folder to put the sketches in and then gives me this
```
Exception in thread "main" java.lang.NullPointerException
    at processing.app.Base.getTarget(Base.java:1624)
    at processing.app.Base.getBoardPreferences(Base.java:1662)
    at processing.app.Base.<init>(Base.java:271)
    at processing.app.Base.main(Base.java:183)

```
  what is the version of java installed on your system ?

Regards,
Abhinav

---

### Post by kaloasd on 2012-11-29
I get this from the terminal
[CODEjava -version
java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.10.1)
OpenJDK 64-Bit Server VM (build 23.2-b09, mixed mode)][/CODE]

---

### Post by Abhinav Kumar on 2012-11-29
Hi,

are you using the 32 or 64 bit system?

Regards,
Abhinav

---

### Post by kaloasd on 2012-11-30
64 bit but I have the necessary 32 bit libraries listed in the wiki
[http://www.chipkit.org/wiki/index.php?title=MPIDE_Installation](http://www.chipkit.org/wiki/index.php?title=MPIDE_Installation)

---

### Post by dino99 on 2012-11-30
check that you have really followed the wiki:

sudo apt-get install librxtx-java
sudo apt-get install ia32-libs-multiarch 
sudo  apt-get install libreadline6
sudo  apt-get install libelfg0

---

### Post by kaloasd on 2012-11-30
Thank you for the replies

I have those libs. I tried installing them again and it said they were installed but I have "ia32-libs-multiarch:i386" I don't know if that's important

---

### Post by kaloasd on 2012-12-27
is there any chance that this would work in wine

---

