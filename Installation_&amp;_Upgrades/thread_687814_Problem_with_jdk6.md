---
title: "Problem with jdk6"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by spar13 on 2008-02-04
hi all,

i'm trying to install sun jdk6 but i cant :( may anyone help me? thaks and sorry for my english :)

---

### Post by Odrodzona-Sarmacja on 2008-02-04
It would help, if you wrote about errors you get, when trying to install that package.

---

### Post by spar13 on 2008-02-04
> **Odrodzona-Sarmacja said:**
> It would help, if you wrote about errors you get, when trying to install that package.

i try to dto what is write in thise site [http://webred.altervista.org/blog/?p=21](http://webred.altervista.org/blog/?p=21). At last there was a message with the license of sun. there was a OK, i press "enter"," "Y" but nothing. then i try to redo evrything but i cant:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
spar@spar-laptop:~$ dpkg --configure -a
dpkg: l'operazione richiesta necessita dei privilegi di superuser

:(

---

### Post by taurus on 2008-02-04
Make sure you have all the repos enable in /etc/apt/sources.list.

Click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code, and the Cdrom in the window below.  Close it and press Refresh.  Now, in the Search field, type **sun-java6-jdk** and install it there.

---

### Post by taurus on 2008-02-04
> **spar13 said:**
> i try to dto what is write in thise site [http://webred.altervista.org/blog/?p=21](http://webred.altervista.org/blog/?p=21). At last there was a message with the license of sun. there was a OK, i press "enter"," "Y" but nothing. then i try to redo evrything but i cant:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
spar@spar-laptop:~$ dpkg --configure -a
dpkg: l'operazione richiesta necessita dei privilegi di superuser

:(

```
**sudo**  dpkg --configure -a
```

p.s.  You need to highlight the <OK> first by pressing the Tab key.  Then, hit Enter.

---

### Post by spar13 on 2008-02-04
thanks all!

I did all the steps again and i hope to have install jdk. Is there any way to controll that is OK?

---

### Post by spar13 on 2008-02-04
i go to /usr/lib/jvm/ and there are too diretorys java-6-sun and java-6-sun-1.6.0.0.3 is normal?

---

### Post by taurus on 2008-02-04
Let's see which one you are using as your default.  Can you post the outputs of these two commands from a terminal?

```
java -version
sudo update-alternatives --config java
```

---

### Post by spar13 on 2008-02-04
> **taurus said:**
> Let's see which one you are using as your default.  Can you post the outputs of these two commands from a terminal?

```
java -version
sudo update-alternatives --config java
```

spar@spar-laptop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

spar@spar-laptop:~$ sudo update-alternatives --config java
Ci sono 2 alternative che forniscono `java'.

  Selezione    Alternativa
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Premi invio per mantenere il default[*], o inserisci il numero da selezionare:2
Uso `/usr/lib/jvm/java-6-sun/jre/bin/java' per fornire `java'.

Sorry but is in italian, it says that are 2 alternative for java 1 and 2, press enter for selecting the defalt or the number for the alternative. I pressed 2. My java is ok now?

---

### Post by taurus on 2008-02-04
Looks like everything is good to go for you with java.  However, you installed the jre version instead of jdk, just so you know.

---

### Post by spar13 on 2008-02-04
> **taurus said:**
> Looks like everything is good to go for you with java.  However, you installed the jre version instead of jdk, just so you know.

so i dont have install jdk? so i cant complie?

---

### Post by spar13 on 2008-02-04
I make some test and its seems ok. thanks a lot taurus :)

---

### Post by ferrarivslamborghini on 2008-03-13
I'm also having the same problems and I tried to do everything that was suggested on this thread but I had no luck.

So firstly I'm getting this message ......

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 sun-java6-bin        

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 java-common          Base of all Java packages
 odbcinst1debian1     Support library and helper program for accessing odbc ini
 unixodbc             ODBC tools libraries
 gcc-3.3-base         The GNU Compiler Collection (base package)
 libstdc++5           The GNU Standard C++ Library v3

And here is the Java version 

stefan@stefan-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
[sudo] password for stefan:
**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. **
stefan@stefan-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

The part in bold is the main problem because I am unable to check updates because the same error pops up.  When I tried to follow the one hint to go to system->administration->synaptic package manager I get this same error**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ** and E:_cache->open ()failed, please report.

If anyone could help I would be greateful !!

---

### Post by ferrarivslamborghini on 2008-03-13
please help asap because it won't let me install any new updates either :(

---

