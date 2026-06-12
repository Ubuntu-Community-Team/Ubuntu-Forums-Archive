---
title: "Install older Sun Java JRE/JDK 6 on Ubuntu Server 10.04"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by fedajkin on 2011-05-12
Hi there, I spent last day by searching an answer to the following question but couldn't find any useful answer at all:
  I installed Ubuntu Server 10.04.2 LTS 64-bit. I added the partner repository for Sun Java. I installed sun-java6-jre and sun-java6-jdk. Unfortunately the version installed is 6 update 21 which is not supported by my version of JIRA so JIRA didn't start (JIRA needs Sun Java newer than update 10 and older than update 21). Is there a way how to easily install update 20?
  What I tried:                                                                                                
  [FONT=Calibri]1)     1)  [/FONT]Download those versions from Sun/Oracle repositories as *.bin and install. This went well but at the end the process created a folder structure with files and java didn’t work at all (java –version returned that java doesn’t exist)
  [FONT=Calibri]2)     2) [/FONT]Experiment with apt-get install sun-java6-jdk/jre=1.6.0_20 etc. No luck.
  [FONT=&quot]3)      3) [/FONT]Experiment with [FONT=Calibri]update-java-alternatives. No luck.[/FONT]
  Please help.

---

