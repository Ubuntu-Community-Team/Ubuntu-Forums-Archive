---
title: "Java installation help"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by marcinpisz1 on 2006-03-13
:confused: As sun's version of the jdk is no longer in any ubuntu repositories I would like to install the environemnt paths to java.  Right now for some strange reason jre 1.4 is installed.  I would like to hcange that to jdk 1.5 that I installed with netbeans package into /opt/jdk and irrelavent but I also put netbeans into opt/netbeans.  How any where do I put the environemntal variables.  

In mandriva I just put  file java.sh into /etc/profile.d/java.sh with the following contents.
JAVA_HOME=/opt/java/jre1.5.0_03
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
How do I do this in ubuntu? 

P.S. I wished this forum had a spell checker.

---

### Post by marcinpisz1 on 2006-03-13
Oh yeah, I would like all users to have access to java on login.

---

