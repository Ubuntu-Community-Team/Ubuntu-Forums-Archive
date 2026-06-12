---
title: "Java Applications Take 100% CPU"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by CalderCoalson on 2008-11-17
After installing two Java applications that I used commonly in Hardy, (jMemorize and jDip), I noticed that an instance of either occupies 100% of my 200% total Dual-Core system.  As expected, 2 instances of either, or one of each will consume the full 200% CPU.  Other applications run fine, so it must be properly yielding CPU-cycles, but it's really annoying because I'm using a laptop and it gets hot and significantly decreases the battery life.  Any help would be greatly appreciated, and I'll try and give you whatever information you need to figure this out.

Thanks
-Calder Coalson

---

### Post by jamesstansell on 2008-11-17
Hi Calder,

It would help if you gave enough information that someone could reproduce the issue.  Can you be specific about exactly what and how you installed, how you run it, any output or logging it produces, which jvm and arguments are used, 32-bit or 64-bit, graphics card and driver, compiz enabled or not, etc.  Even if you don't have a clue about some of that stuff, it's fine; just start with what you can.

I've seen one report that sounded similar - if I recall correctly it was for one of the java plugins running in firefox.  They saw 100% cpu used but the system remained responsive.

Regards,

-james.

---

### Post by CalderCoalson on 2008-11-18
> **jamesstansell said:**
> 
It would help if you gave enough information that someone could reproduce the issue.  Can you be specific about exactly what and how you installed, how you run it, any output or logging it produces, which jvm and arguments are used, 32-bit or 64-bit, graphics card and driver, compiz enabled or not, etc.  Even if you don't have a clue about some of that stuff, it's fine; just start with what you can.


**Installation**
Installed jMemorize from a .deb, didn't have Java so the process looked something like
```
sudo dpkg -i jMemorize*.deb
sudo apt-get -f install
```
Then downloaded a .jar file of jDip, and placed it in ~/.jdip

**Running**
I run jDip using
```
cd ~/.jdip; java -jar jdip.jar
```
jMemorize is run from the bin file.

**Logs**
Where would I find these?

**JVM Arguments**
I assume you mean like "-jar"?  Described in "Running".

**Operating System**
Ubuntu 8.10 using kernel 2.6.27-8-generic 64-bit

**Graphics Card**
GeForce 7150 / nForce 630M/PCI/SSE2
As far as I can tell, I'm using the NVidia Proprietory driver version 177 with it.

**Compiz**
Enabled

I hope some of this helps...

---

### Post by ilyasergey on 2008-11-21
Hello,
I have same behaviour using IntelliJ IDEA with Intrepid. It doesn't depends on current Java (I tried both Sun distribution and Open JDK). Judjing by profile snapshot the class sun.java2d.SunGraphics2D class' methods take major part of CPU.
Thanks in advance.

With best regards,
Ilya

---

### Post by CalderCoalson on 2008-11-25
Replacing OpenJDK with Sun-Java works solved this issue and many others:
```
sudo apt-get install sun-java6-bin
sudo update-java-alternatives --set java-6-sun
```

---

