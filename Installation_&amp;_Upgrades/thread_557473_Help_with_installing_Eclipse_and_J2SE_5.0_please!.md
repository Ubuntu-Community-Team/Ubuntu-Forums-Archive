---
title: "Help with installing Eclipse and J2SE 5.0 please!"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by spearfish on 2007-09-22
Help!  I can't find two programs that I just installed!

I have Ubuntu 7.04 on my Dell desktop, and using the Synaptic Package Manager, I thought that I installed the following:

1. sun-java5-jdk (Sun Java 5.0 development kit)
2. ecj (Standalone version of Eclipse)

What I'm wondering is, where IS this stuff? Eclipse doesn't show up under Applications->Programming. Also, when I type "java -showversion" in a terminal window, it says I am running java 1.4. Huh? Where is J2SE 5.0 and where is Eclipse?

Thanks for ANY help on this!

---

### Post by matthew.lns1 on 2007-09-22
Try running eclipse with "Run Application". You activate it by holding down the ALT and CRTL key simultaneously. Type "ecj" in the text box and you should be set. Try typing in "javac -version". Maybe that will work. Just as a side note: almost all applications install in 
"/usr/bin/" or at least there executable's do.

---

### Post by spearfish on 2007-09-22
Ok I think I answered my own question.  The Synaptic Package Manager is worthless for installing Java and Eclipse.  I had to type the following commands into a terminal window:

sudo update-java-alternatives -s java-6-sun

sudo apt-get install eclipse

That got both Java and Eclipse running.  (sigh)  I wish the Ubuntu developers would get the Synaptic Package Manager working right.  It sucked in Ubuntu 5.10 and it still doesn't do the job in Version 7.04.
(grumble) 

:)

---

