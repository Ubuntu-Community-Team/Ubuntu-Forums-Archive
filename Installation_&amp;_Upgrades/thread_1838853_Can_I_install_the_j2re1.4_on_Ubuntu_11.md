---
title: "Can I install the j2re1.4 on Ubuntu 11?"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by JoeSabido on 2011-09-04
I would like to update a couple of computers at work which are using Ubuntu 6 with Java 1.4 to Ubuntu 11.

On those computers there's a software that they use, which is developed in Java and REQUIRES version 1.4 of the JRE. 

Such software was developed by an external company so I don't know why the REQUIRE 1.4, but they do.

My question is, after a fresh install of Ubuntu 11, can I install Java 1.4? If so, how?

Thanks!

---

### Post by raja.genupula on 2011-09-04
yes you can install . you can keep current and required versions of java in your system .

---

### Post by sanderd17 on 2011-09-04
Don't they require java 1.4 or above? Java stays backwards compatible.

You could try a test system first.

Installing Java 1.4 should be possible, but not advisable.

---

### Post by JoeSabido on 2011-09-04
> **sanderd17 said:**
> Don't they require java 1.4 or above? Java stays backwards compatible.

You could try a test system first.

Installing Java 1.4 should be possible, but not advisable.

We installed the software on a system that has Java 1.6 and we had a few problems. It is possible that the software is a piece of crap but in the meantime we're stuck with it. The software company told us to stay with Java 1.4

What's the latest Ubuntu version that will support java 1.4?

Thanks.

---

### Post by lykeion on 2011-09-04
You won't find any Ubuntu versions supporting Java 1.4, since not even Oracle supports it any longer. You can however download and install Java 1.4 manually from Oracle archive pages: [HERE]("http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javase14-419411.html#7501-j2sdk-1.4.2-oth-JPR").
But I'd say the problem is with the Java software, and the company behind it that claims it needs Java 1.4. I don't think installing and running it with Java 1.4 will solve the problem.

---

### Post by JoeSabido on 2011-09-04
> **lykeion said:**
> You won't find any Ubuntu versions supporting Java 1.4, since not even Oracle supports it any longer. You can however download and install Java 1.4 manually from Oracle archive pages: [HERE]("http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javase14-419411.html#7501-j2sdk-1.4.2-oth-JPR").
But I'd say the problem is with the Java software, and the company behind it that claims it needs Java 1.4. I don't think installing and running it with Java 1.4 will solve the problem.

The software currently runs fine with Java 1.4, when I run it with a newer version of Java (1.6 for example) it doesn't work right.

The software has a config file where you can point to the directory of the Java install.

So, can I download one of the bin files for the 1.4 from the URL you gave me, extract it to a directory and just point the software to that without installing it system-wide?

---

### Post by lykeion on 2011-09-04
I guess you could do that, if you can set Java path for your software.
Remember that the downloaded .bin-file from Oracle it's not a zip archive, you need to run it in a terminal:
1. make it executable 
```
chmod u+x j2sdk-<version>.bin
```
2. run it (after accepting license it will extract into current dir)
```
./j2sdk-<version>.bin
```

---

### Post by recluce on 2011-09-04
> **sanderd17 said:**
> Don't they require java 1.4 or above? Java stays backwards compatible.


In theory. In reality, this is not true. For example, I have a virtual Windows XP machine to use Cisco's SDM for simple router configurations. This requires JRE 1.4 as well. Anything later - and the Cisco SDM will fail.

---

### Post by JoeSabido on 2011-09-04
> **lykeion said:**
> I guess you could do that, if you can set Java path for your software.
Remember that the downloaded .bin-file from Oracle it's not a zip archive, you need to run it in a terminal:
1. make it executable 
```
chmod u+x j2sdk-<version>.bin
```
2. run it (after accepting license it will extract into current dir)
```
./j2sdk-<version>.bin
```

I'll give that a try tomorrow and let you know how it went.

Thanks :)

---

