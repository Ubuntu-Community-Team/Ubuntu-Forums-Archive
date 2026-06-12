---
title: "Netbeans IDE 6.9.1 Installing Help"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2010-09-26
Hi,

I downloaded netbeans ide 6.9.1 and ran the file, it started the installer and the wizard pops up, but then the installer just aborts. I dunno how to make it work. Any ideas?

---

### Post by mwildam on 2010-09-27
Do you have a java jdk installed?
Maybe it only works with the Sun/Oracle one, but I don't think so - worked with the OpenJDK in the past also. But: I noticed that while for the desktop install openjdk is installed by default, on the netbook remix is not! - Maybe because poorly powered netbooks run java too slow - don't know - never tested.

So I guess you don't have any Java runtime installed!

Here is, how I do NetBeans installations - and that worked also on my NetBook: [http://it-tactics.blogspot.com/2010/09/install-netbeans-on-ubuntu-1004.html](http://it-tactics.blogspot.com/2010/09/install-netbeans-on-ubuntu-1004.html)

---

### Post by Unterseeboot_234 on 2010-09-27
I do Synaptic sun-jdk-nonfree and that puts a system-wide jre to run java, .jars, applets from the Terminal and from web pages. That gets buried in opt/... this also installs ia32 if I am 64-bit.

Then to make code, I like a fully accessible JDK and project folder in Home. (I do not want to mess with file permissions while sweating code.) So I download the JavaSE (or EE) jdk-Netbeans bundle, saving the bin in Home. Install to folders: ~JDK1.6_22, ~Netbeans 6.9.x, ~Netbeans_projects.

The Netbeans will have to produce a final .jar to run universally, but working code will run in the IDE and give you more options.

---

### Post by psycho5 on 2010-09-27
Yes, I managed to get it to work.

From Sun's website I downloaded the bundle netbeans 6.9.1 with jdk version 6 update 21, and I installed java first to my home directory then installed netbeans with the --java /directory attribute.

---

