---
title: "Java 1.5 in fiesty"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Zanik221 on 2007-04-30
In both Dapper and Edgy, it took all of 5 minutes to install Sun's Java 1.5 SDK.  Now, in fiesty, I can't seem to replace the GNU jdk with Sun's.  Previously, I could just install the Sun JDK with APT and it'd work fine.  Now, no matter what I do, I'm still stuck with GNU, which is only java 1.4 compatible.  I have, currently, two school projects which greatly depend on my having java 1.5, so you can imagine how frustrating this is for me.

I'd appreciate any help anyone can offer.

---

### Post by xlinuks on 2007-04-30
That is pretty easy, in fact you don't even have to uninstall GNU Java.
Do the following, since you need 1.5 and the default is already 1.6 you'll have to search for 1.5, but here's the direct link:
[http://java.sun.com/javase/downloads/index_jdk5.jsp](http://java.sun.com/javase/downloads/index_jdk5.jsp)
on this page choose to download "JDK 5.0 Update 11" (without NetBeans nor Java EE since you most probably don't need them and it will take less to download).
- Press on the right button 'Download'.
-Before downloading notice the above _red_ word "Required", choose "Accept" and the page will load once again.
-Now you choose your Linux version, but _not_ the RPM version, but the simple .bin version (Linux self-extracting file, jdk-1_5_0_11-linux-i586.bin, size 47.28 MB).
After download is finished you only unpack it from the command line and you're done. Now create a soft link of the java executables (java and javac) into your /home/yourname/bin directory so that running "java" or "javac" from any command line will now use SUNs JDK 1.5, not the GNU JDK.
Feel free to ask.

---

### Post by TheWizzard on 2007-04-30
try running
sudo update-alternatives --config java

---

