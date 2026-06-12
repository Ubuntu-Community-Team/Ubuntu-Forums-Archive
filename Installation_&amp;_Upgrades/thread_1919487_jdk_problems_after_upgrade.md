---
title: "jdk problems after upgrade"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by learning_ on 2012-02-02
Ok, here's my dilemma :-k :
I need the current version of jdk installed (1.7.0_02) and I followed these tutorials 
[http://www.shinephp.com/install-jdk-7-on-ubuntu/]("http://www.shinephp.com/install-jdk-7-on-ubuntu/") 
[http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html#install-64](http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html#install-64)
and I forgot to select 1.7.0_02 as the version to use so when I ran the java -version command it returned ```
java version 1.6.0_20
``` but that isn't the problem. After I went back into --config java and fixed that by selecting 1.7.0_02, I tried to find the version again with java -version and now I get this ```
bash: /usr/bin/java: cannot execute binary file

``` ](*,)

I can't find any solution anywhere else. PLEASE someone help!

---

### Post by learning_ on 2012-02-03
ok so this may have seemed obvious but it didn't click until I was just staring at this wall of commands that I put in last night: somehow the java.bin was removed from the /usr/bin/ directory but that's about all I know. I don't even know what that means or how to even start to try and fix it. Any ideas anyone?

---

### Post by learning_ on 2012-02-03
so is this one still active? I really need to get this straightened out asap...

---

### Post by cortman on 2012-02-03
Why not just install it from the repositories?

```
sudo apt-get install openjdk-7-jdk
```

---

### Post by learning_ on 2012-02-03
it's not in the repositories. Or at least not in the repositories I have and I couldn't find anything about adding one that has openjdk-7

---

### Post by cortman on 2012-02-03
> **learning_ said:**
> it's not in the repositories. Or at least not in the repositories I have and I couldn't find anything about adding one that has openjdk-7

Run

```
sudo apt-get update
```

And then the code I pasted above. It should work.

---

### Post by learning_ on 2012-02-03
> **cortman said:**
> Run

```
sudo apt-get update
```

And then the code I pasted above. It should work.

did, and got this
```
E: Couldn't find package openjdk-7-jdk

``` just like I said, it's not in my repositories...

---

### Post by cortman on 2012-02-04
Then run

```
apt-cache search openjdk
```

And see what the package is called according to your repositories.

---

### Post by learning_ on 2012-02-04
This is what I get.
```
cacao-source - Source for CACAO, a Java virtual machine
default-jdk - Standard Java or Java compatible Development Kit
default-jdk-doc - Standard Java or Java compatible Development Kit (documentation)
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
freemind - Java Program for creating and viewing Mindmaps
icedtea-6-jre-cacao - Alternative JVM for OpenJDK, using Cacao
icedtea6-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
openjdk-6-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-6-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-6-doc - OpenJDK Development Kit (JDK) documentation
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-6-jre-lib - OpenJDK Java runtime (architecture independent libraries)
openjdk-6-source - OpenJDK Development Kit (JDK) source files
openjdk-6-jre-zero - Alternative JVM for OpenJDK, using Zero/Shark

```

Do you happen to know where I can find a repository with openjdk7?

---

### Post by learning_ on 2012-02-04
And before the inevitable "just google it," google has forsaken me on this one... hence my resorting to the forums.

---

### Post by doobrie on 2012-02-04
Do you have the Universe repository enabled?  I think it's in that one.

---

### Post by learning_ on 2012-02-04
I don't believe so... how do I go about checking that/enabling it?

EDIT: is the attached picture what you are referring to?

---

### Post by cortman on 2012-02-04
> **learning_ said:**
> I don't believe so... how do I go about checking that/enabling it?

EDIT: is the attached picture what you are referring to?

Yes sir!

---

### Post by learning_ on 2012-02-04
Even after updating that, still found nothing about openjdk-7...

---

### Post by learning_ on 2012-02-04
Would it be better/easier to just upgrade to oneric and just try from that side?

---

### Post by cortman on 2012-02-04
You need to check the "Partner" repositories. Then run

```
sudo apt-get update
```

and see if you can get it then.

EDIT: This probably won't work now, what with Canonical and Oracle not getting along so nicely. [This page]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") has detailed instructions on how to install it.

---

### Post by learning_ on 2012-02-04
No luck. It still can't see anything related to openjdk 7. I did mention I'm on 10.04 right?

EDIT: found [this]("http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html") and [this]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") linked from a blog which was linked from another blog which was linked from someone's post in the forums... kinda a lucky find really. so I followed the guide for downloading from their ppa repository and it seems to have worked but when running ```
java -version
``` it still returns ```
bash: /usr/bin/java: cannot execute binary file
```

what did I screw up?

---

### Post by cortman on 2012-02-04
This is after running

```
sudo update-java
```

?
Make sure the file permissions are set to executable for /bin/java.

---

### Post by learning_ on 2012-02-04
> **cortman said:**
> This is after running

```
sudo update-java
```

?
Make sure the file permissions are set to executable for /bin/java.

That update command is not recognized... but after some digging in the bin directory via terminal I found all the necessary java binaries (listed as bright green if that matters) but I cannot find them via nautilus.

EDIT: ran ```
ls -l /usr/bin/
``` to find the set permissions on the individual files and all the java related ones have output that looks like this: ```
 lrwxrwxrwx 1 root   root          22 2012-02-02 17:57 java -> /etc/alternatives/java
```

---

### Post by learning_ on 2012-02-04
It seems somehow the java bins have been moved or hidden or something... I'm not exactly sure what's going on with it. Any ideas?

---

### Post by cortman on 2012-02-04
> **learning_ said:**
> Would it be better/easier to just upgrade to oneric and just try from that side?

I hate to throw in the towel but I'm running out of ideas at this point. This may not be the worst idea. When I'm not on my mobile I'll look up that jdk-7 installation in detail.

EDIT:How about you try the procedure outlined in post 16- checking "partner" repositories and running apt-update. Open jdk should still be available.

---

### Post by learning_ on 2012-02-05
Yes I did try to do that when you posted it. I enabled partner repositories and even added a repository from [http://www.webupd8.org]("http://www.webupd8.org/")
for java/ jdk 7 and it seems to have installed properly but still the binaries are not available to be accessed for whatever reason as I said in post [17]("http://ubuntuforums.org/showpost.php?p=11663823&postcount=17") and [19]("http://ubuntuforums.org/showpost.php?p=11663908&postcount=19") 

I'm thinking I may need to have this thread moved to a different forum...?

---

### Post by cortman on 2012-02-06
> **learning_ said:**
> Yes I did try to do that when you posted it. I enabled partner repositories and even added a repository from [http://www.webupd8.org]("http://www.webupd8.org/")
for java/ jdk 7 and it seems to have installed properly but still the binaries are not available to be accessed for whatever reason as I said in post [17]("http://ubuntuforums.org/showpost.php?p=11663823&postcount=17") and [19]("http://ubuntuforums.org/showpost.php?p=11663908&postcount=19") 

I'm thinking I may need to have this thread moved to a different forum...?

I'm thinking you may need to either upgrade to Oneiric or just use openjdk 6. Unless there's something that specifically needs jdk-7, 6 should work fine.

---

### Post by learning_ on 2012-02-08
Taking a programming class and they require the latest java utilities for our programs... I don't understand why. Thanks for the effort though. I'll just upgrade over the weekend.

---

