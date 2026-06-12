---
title: "Ubuntu 9.10 Unable to play sounds on LimeWire / FrostWire"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Enav on 2010-02-16
Description:
-----------------
- Every time you want play or preview some audio file on LimeWire/Frostwire its do not work and some times this makes crash the sound system 

Details:
 -----------------
- JVM = Java Virtual Machine
-  LimeWire/Frostwire are programs based on the Java platform and they need JVM to work
- "java-6-sun" is the official Sun's JVM but some parts of this package are closed source code (about 4%)
- "java-6-openjdk" is a open source code implementation (100% open source)
- Ubuntu 9.10 actually have installed and running  "java-6-openjdk" and "java-6-sun" same time
- Ubuntu 9.10 by default use "java-6-openjdk" 
  - In this case "java-6-openjdk" have some audio bugs  
- To solve this problem you only need to make "java-6-sun" the system default JVM instead of "java-6-openjdk"

Solution:
 -----------------
1- Close all programs
2- Open terminal
3- Run:      sudo update-alternatives --config java
That is going to show you something like this:

```
There are 2 choices for the alternative java (providing /usr/bin/java).
Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode
Press enter to keep the current choice
[*], or type selection number:
```4- Enter the number relating to "java-6-sun" option and press [Enter] key
5- Restart Ubuntu
6- Open LimeWire/FrostWire and test some audio files
7- Enjoy :)


:arrow: Remember to send a reply, if this information solved your problem

---

### Post by Enav on 2010-02-16
Sorry - the post above is not working completely
this just make the Java sounds works for some minutes and crash the sound system again
:icon_frown:

---

### Post by ve7eme on 2010-08-31
Solved, and am using Linux Mint 9, and Frostwire 4.20 from Frostwire Web site
Thanks :KS

---

### Post by ve7eme on 2010-11-20
:p Solved Thanks for the tip, Frostwire 4.21 and LM9

Darrel

---

