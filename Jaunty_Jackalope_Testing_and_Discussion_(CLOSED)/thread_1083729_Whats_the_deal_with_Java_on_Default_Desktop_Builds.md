---
title: "Whats the deal with Java on Default Desktop Builds"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-03-01
Can someone please clarify.

I went to the terminal for:

```
java -version
```

And came back with an error. So I go into synpatic and I see that openjdk, sun's jre/jdk, icedtea etcetc are all not installed???? Cant recall offhand if I messed with it on my test box.

While were at it, I see netbeans is up to date in the repos but eclipse isnt, so has anyone got any strong opinions about which IDE I should install?

---

### Post by taavikko on 2009-03-01
```
java -version
java version "1.6.0_12"
Java(TM) SE Runtime Environment (build 1.6.0_12-b04)
Java HotSpot(TM) 64-Bit Server VM (build 11.2-b01, mixed mode)
```

I had the same issue a while back, but obviously some update has cleared that issue...

IDE for java... *shivers* :D
I would go with eclipse.

---

### Post by JohnJackson on 2009-03-01
NetBeans!

---

### Post by zorkerz on 2009-03-25
I have jaunty installed and it does not appear to have java installed at all. 'java -version' returns this.
```

The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * cacao-oj6-jre-headless
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
```
So somehow java was uninstalled or never installed.

What version of java should I install?
What version comes default on a new Jaunty install?

---

### Post by cl333r on 2009-03-25
Unlike mono, by default Java is not installed in Ubuntu. There are several versions of Java. The fastest and most trouble-free version is Java from Sun, to install it:
```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-jdk
```

note: sun-java6-jdk is only needed if you're a Java developer.

---

### Post by zorkerz on 2009-03-25
Oh thanks. I wonder why I thought it was installed in Jaunty.

---

### Post by directhex on 2009-03-25
> **cl333r said:**
> Unlike mono, by default Java is not installed in Ubuntu. There are several versions of Java. The fastest and most trouble-free version is Java from Sun, to install it:
```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-jdk
```

note: sun-java6-jdk is only needed if you're a Java developer.

Please note that sun-java6-* might be the "fastest and most trouble-free", but they're also proprietary closed-source software. The closest Free equivalent, based on mostly the same source code, comes from openjdk-6-jre, icedtea6-plugin (and openjdk-6-jdk)

Java is not included in a default Ubuntu install for one major reason, and one minor one - major reason is it's massively bloated (over 100 meg to install a minimal Java capable of 'hello world', i.e. there's not actually room on the CD), minor reason is it's not very cross-platform (no usable PowerPC port of OpenJDK)

---

### Post by zorkerz on 2009-03-25
Thanks that application makes so much sense. Ive never had a clear idea why it was not included. What is the state of icedtea? In the past my experience is that it did not do so well but that was at least a year ago.

---

### Post by directhex on 2009-03-25
> **zorkerz said:**
> Thanks that application makes so much sense. Ive never had a clear idea why it was not included. What is the state of icedtea? In the past my experience is that it did not do so well but that was at least a year ago.

In my experience it's nowhere near as good as the Sun plugin - but I'm on AMD64, so I haven't had access to a Java plugin for ages ANWYAY

---

### Post by zorkerz on 2009-03-25
Oh so sun does not make an x86-64 version of java? Thats what im running.

---

### Post by loomsen on 2009-03-25
Mine is working just fine with the current snapshot release...

[Download here](http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.bin)

make it executable and execute it in the directory it should be installed to. 
(For me this is: 
/opt/java64/
so u might have to change this path if u consider giving it a try)

Then do sth like:
```

sudo update-alternatives --install /usr/bin/java java /opt/java64/jre1.6.0_14/bin/java 10
```

to populate it.
If you already have a pkg providing java, run:
```
sudo update-alternatives --config java
```
and choose the apropriate path.

To use it with opera I specified 
/opt/java64/jre1.6.0_14/lib/amd64
as java path
(Tools-->Preferences-->Advanced-->Content-->Java Options-->Java Path)

To check, click validate path, and opera will tell:

*The Java path seems to specify a valid directory.*

Another check:
> 
[color=red]docter[/etc/alternatives][/color] java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b12, mixed mode)
[color=red]docter[/etc/alternatives][/color] 

and yet another:
> 
[color=red]docter[~][/color]  ls -l /usr/bin/java ; ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 22 2009-03-26 01:09 /usr/bin/java -> /etc/alternatives/java
lrwxrwxrwx 1 root root 32 2009-03-26 02:11 /etc/alternatives/java -> /opt/java64/jre1.6.0_14/bin/java
[color=red]docter[~][/color] 


To launch JDownloader for instance, 
```
java -jar <path>/<to>/<installdir>/JDownloader.jar
```

---

### Post by directhex on 2009-03-26
> **zorkerz said:**
> Oh so sun does not make an x86-64 version of java? Thats what im running.

They make AMD64 Java. But the official plugin has been a TODO item since 2002 - I believe Java 6 Update 12 introduced it. Intrepid only includes U10, so you need to run Jaunty for the official Sun plugin on AMD64

---

### Post by rbmorse on 2009-03-26
Sun just released update 13. 64-bit parts listed.  Available at [www.java.com]("http://www.java.com")  Install per above.

---

