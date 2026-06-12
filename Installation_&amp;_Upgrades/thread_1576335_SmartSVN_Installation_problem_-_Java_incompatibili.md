---
title: "SmartSVN Installation problem - Java incompatibility"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by elexhobby on 2010-09-17
I downloaded SmartSVN from the website, and when I try running the smartsvn.sh file, I get the following error:

> 
Disabling SSE42Intrinsics to work-around bug 6875866.
An incompatible Java version has been detected which has been reported to cause strange bugs. Aborting now. To force SmartSVN to use this Java version, set the VM property smartsvn.checkIncompatibleJava to false (use at your own risk).

Please install the latest release of the SUN Java SE Runtime Environment (JRE) from:
[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)
or if it is already installed, make sure it is used.

I get the same error on two computers - one running Lucid, the other running Hardy. Both of them have the latest version of Java installed. Could somebody give me insight into what's wrong?

Thanks a lot!

---

### Post by lykeion on 2010-09-17
Hi
I checked the documentation on the SmartSVN homepage and it says:
"Ensure, that an up to date JRE from SUN is installed on your system. Some systems, e.g. Fedora, ship with GCJ (GNU libgcj) or beta version of OpenJDK which are not sufficient. 
On Ubuntu systems use Synaptic to install the Java Runtime Environment 1.6.0 from SUN (package "sun-java6-jre" from the "multiverse" repository)."

So it seems it requires Sun Java and not the default installed OpenJDK Java.

In Hardy > Karmic it's found in the multiverse repository so you can install the "sun-java6-jre package with Synaptic.

In Lucid it's moved to the partner repository which you have to enable first, like this:
System > Administration > Software Sources > Other Software tab > Check the entry ending with partner.
Then you can install the "sun-java6-jre package with Synaptic.

You can have several Java JREs installed at the same time. See this page on how to choose the default version:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

My suggestion is however to uninstall the OpenJDK first, then install the Sun Java. In Synaptic do a quick search for packages starting with "openjdk" and remove them. Then install the package sun-java6-jre.

Good luck

EDIT
Saw that you already posted this question in another thread:
[http://ubuntuforums.org/showthread.php?t=1576027](http://ubuntuforums.org/showthread.php?t=1576027)

Please do not cross post, or post the same thing in multiple locations.

---

### Post by elexhobby on 2010-09-22
Thanks a ton, lykeion! I did as you suggested and everything worked like a charm.

And sorry about the repost. I'll avoid it in the future.

---

