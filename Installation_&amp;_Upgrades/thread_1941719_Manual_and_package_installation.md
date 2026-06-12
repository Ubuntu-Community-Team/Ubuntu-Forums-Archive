---
title: "Manual and package installation"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by huu2011 on 2012-03-16
Hello all,
Iam learning ubuntu and installed ubuntu 11.10 desktop.
Installing software through package or repositories make it is for another software which will install later to detect.but install manual software like tomcat,later on installed the software which use it.then it giving me error that apache-tomcat is now well installed.My question is
How can I make manual installations be detected by software uses it?.
should I add in environment?. which environment?.
NB.The program I want to install is apache-tomcat and oracle java.

please any idea or hint?
thank you
huu

---

### Post by mraandtux on 2012-03-16
Synaptic is recommended when installing packages, sudo apt-get install synaptic

---

### Post by huu2011 on 2012-03-16
hello mraandtux
thank you for your answer.Yes, I have been using it.Now I have manual installed tomcat 6.0.32 and java in /usr/local directory.but there is one programe trying to install but cannot detect those installed program.How can I make it detectable?
thank you again

---

### Post by mraandtux on 2012-03-16
> **huu2011 said:**
> hello mraandtux
thank you for your answer.Yes, I have been using it.Now I have manual installed tomcat 6.0.32 and java in /usr/local directory.but there is one programe trying to install but cannot detect those installed program.How can I make it detectable?
thank you again
Try to look at the "Installed" fliter.

---

