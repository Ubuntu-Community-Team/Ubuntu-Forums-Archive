---
title: "Updating a standalone Ubuntu 14.04.1 LTS station"
date: 2014-10-23
forum: Installation &amp; Upgrades
---

### Post by Jean-Jacques_Rodot on 2014-10-23
Hello,

I' trying to install java on a _standalone _station with Ubuntu 14.04.1 LTS installed.
1/ I can't connect this Ubuntu station on internet.
2/ For download I have a Windows XP connected to internet but with limited administration rights (can't install fancy softwares).
3/ The two machines are 200 meters away, I can't hard-link them or move them, I have to use a USB key and walk... 

When I install *openjdk-7-jdk* it requires *openjdk-7-jre* which requires *openjdk-7-jre-headless* which requires *ca-certificates-java*...
=>I'm lost in an infinite chain of dependencies.

I tried to install Synaptic to list all dependencies once and for all (and hopefully generate a download script), but the *synaptic_0.81.1_i386.deb* I got is not complete : it requires *libept1.4.12* which will surely requires *something *which will requires *another thing*...I'm back to square one.

Where can I get a full comprehensive dependencies listing/script generating tool ?

Thank you for your help.

---

### Post by kc1di on 2014-10-23
Hi Jean-Jacques_Rodot and welcome to Ubuntu,

[This page ]("http://techedemic.com/2012/01/18/installing-java-openjre-6-on-ubuntu-server-without-internet-access/")will guide you through how to install java without an internet connection. (You'll have to download the installer with the internet connected machine but after that you can install it on the other machine.) good Luck :)

---

