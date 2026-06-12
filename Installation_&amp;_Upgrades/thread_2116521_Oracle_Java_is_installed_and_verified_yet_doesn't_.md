---
title: "Oracle Java is installed and verified yet doesn't work"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by bkarlan on 2013-02-16
I have deleted all OpenJDK programs including IcedTea.  I have installed Java via the terminal and can verify in "about:plugins" in both Chrome and Firefox that I have Java(TM) - Version: 1.7.0_13 installed.  I have verified with [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp) that I have Java installed by getting the following message;
Your Java is working
Latest Java installed
Your Java configuration is as follows:
Vendor: Oracle Corporation
Version: Java SE 7 Update 13
Operating System: Linux 3.5.0-23-generic
Java Architecture: 32-bit

Yet it still doesn't work and whenever I run a website that requires Java I'm told I need to install Java.  Additionally, when I go to the site [http://www.java.com/en/download/installed.jsp?detect=jre](http://www.java.com/en/download/installed.jsp?detect=jre) I'm told I do not have Java installed.

Can anyone help?

---

### Post by bkarlan on 2013-02-28
I have now verified Java.  "You have the recommended Java installed (Version 7 Update 15)."

Yet when I try to run a site that requires Java it tells me that it is not installed.  I have told Java to Activate on all sites already.

It verifies with Firefox, but not Chrome.

---

### Post by sixcorners on 2013-02-28
maybe it would help to paste the stuff you find in chrome's about:plugins

---

### Post by bkarlan on 2013-02-28
> **bkarlan said:**
> I have now verified Java.  "You have the recommended Java installed (Version 7 Update 15)."

Yet when I try to run a site that requires Java it tells me that it is not installed.  I have told Java to Activate on all sites already.

It verifies with Firefox, but not Chrome.

I have verified Java;
java version "1.7.0_12-ea"
Java(TM) SE Runtime Environment (build 1.7.0_12-ea-b05)
Java HotSpot(TM) Server VM (build 24.0-b26, mixed mode)

Yet I'm always told on the website the following;
We have detected that you do not have Java installed. At least 1.6.0_11 of the Java Runtime Environment is required to run zipForm&#65533; 6 Professional.

---

### Post by bkarlan on 2013-02-28
> **sixcorners said:**
> maybe it would help to paste the stuff you find in chrome's about:plugins

It shows in Chrome and I have clicked enable.  But the site is not setup to run well in Chrome, so I don't care much about it running in Chrome at this point.

---

### Post by bkarlan on 2013-02-28
> **bkarlan said:**
> It shows in Chrome and I have clicked enable.  But the site is not setup to run well in Chrome, so I don't care much about it running in Chrome at this point.

Here is the data for Firefox from about:plugins;
Java(TM) Plug-in 1.7.0_15

    File: libnpjp2.so
    Version: 
    Java plug-in for NPAPI-based browsers.

MIME Type 	Description 	Suffixes
application/x-java-vm 	Java™ Plug-in 	
application/x-java-applet 	Java™ Plug-in Applet 	
application/x-java-bean 	Java™ Plug-in JavaBeans 	
application/x-java-applet;version=1.1 	Java™ Plug-in 	
application/x-java-bean;version=1.1 	Java™ Plug-in 	
application/x-java-applet;version=1.1.1 	Java™ Plug-in 	
application/x-java-bean;version=1.1.1 	Java™ Plug-in 	
application/x-java-applet;version=1.1.2 	Java™ Plug-in 	
application/x-java-bean;version=1.1.2 	Java™ Plug-in 	
application/x-java-applet;version=1.1.3 	Java™ Plug-in 	
application/x-java-bean;version=1.1.3 	Java™ Plug-in 	
application/x-java-applet;version=1.2 	Java™ Plug-in 	
application/x-java-bean;version=1.2 	Java™ Plug-in 	
application/x-java-applet;version=1.2.1 	Java™ Plug-in 	
application/x-java-bean;version=1.2.1 	Java™ Plug-in 	
application/x-java-applet;version=1.2.2 	Java™ Plug-in 	
application/x-java-bean;version=1.2.2 	Java™ Plug-in 	
application/x-java-applet;version=1.3 	Java™ Plug-in 	
application/x-java-bean;version=1.3 	Java™ Plug-in 	
application/x-java-applet;version=1.3.1 	Java™ Plug-in 	
application/x-java-bean;version=1.3.1 	Java™ Plug-in 	
application/x-java-applet;version=1.4 	Java™ Plug-in 	
application/x-java-bean;version=1.4 	Java™ Plug-in 	
application/x-java-applet;version=1.4.1 	Java™ Plug-in 	
application/x-java-bean;version=1.4.1 	Java™ Plug-in 	
application/x-java-applet;version=1.4.2 	Java™ Plug-in 	
application/x-java-bean;version=1.4.2 	Java™ Plug-in 	
application/x-java-applet;version=1.5 	Java™ Plug-in 	
application/x-java-bean;version=1.5 	Java™ Plug-in 	
application/x-java-applet;version=1.6 	Java™ Plug-in 	
application/x-java-bean;version=1.6 	Java™ Plug-in 	
application/x-java-applet;version=1.7 	Java™ Plug-in 	
application/x-java-bean;version=1.7 	Java™ Plug-in 	
application/x-java-applet;jpi-version=1.7.0_15 	Java™ Plug-in 	
application/x-java-bean;jpi-version=1.7.0_15 	Java™ Plug-in 	
application/x-java-applet;deploy=10.15.2 	Java™ Plug-in 	
application/x-java-applet;javafx=2.2.7 	Java™ Plug-in 	
application/x-java-vm-npruntime 	Java™ Plug-in

---

### Post by Tulainas on 2013-08-04
> **bkarlan said:**
> Here is the data for Firefox from about:plugins;
Java(TM) Plug-in 1.7.0_15

    File: libnpjp2.so
    Version: 
    Java plug-in for NPAPI-based browsers.

MIME Type 	Description 	Suffixes
application/x-java-vm 	Java™ Plug-in 	
application/x-java-applet 	Java™ Plug-in Applet 	
application/x-java-bean 	Java™ Plug-in JavaBeans 	
application/x-java-applet;version=1.1 	Java™ Plug-in 	
application/x-java-bean;version=1.1 	Java™ Plug-in 	
application/x-java-applet;version=1.1.1 	Java™ Plug-in 	
application/x-java-bean;version=1.1.1 	Java™ Plug-in 	
application/x-java-applet;version=1.1.2 	Java™ Plug-in 	
application/x-java-bean;version=1.1.2 	Java™ Plug-in 	
application/x-java-applet;version=1.1.3 	Java™ Plug-in 	
application/x-java-bean;version=1.1.3 	Java™ Plug-in 	
application/x-java-applet;version=1.2 	Java™ Plug-in 	
application/x-java-bean;version=1.2 	Java™ Plug-in 	
application/x-java-applet;version=1.2.1 	Java™ Plug-in 	
application/x-java-bean;version=1.2.1 	Java™ Plug-in 	
application/x-java-applet;version=1.2.2 	Java™ Plug-in 	
application/x-java-bean;version=1.2.2 	Java™ Plug-in 	
application/x-java-applet;version=1.3 	Java™ Plug-in 	
application/x-java-bean;version=1.3 	Java™ Plug-in 	
application/x-java-applet;version=1.3.1 	Java™ Plug-in 	
application/x-java-bean;version=1.3.1 	Java™ Plug-in 	
application/x-java-applet;version=1.4 	Java™ Plug-in 	
application/x-java-bean;version=1.4 	Java™ Plug-in 	
application/x-java-applet;version=1.4.1 	Java™ Plug-in 	
application/x-java-bean;version=1.4.1 	Java™ Plug-in 	
application/x-java-applet;version=1.4.2 	Java™ Plug-in 	
application/x-java-bean;version=1.4.2 	Java™ Plug-in 	
application/x-java-applet;version=1.5 	Java™ Plug-in 	
application/x-java-bean;version=1.5 	Java™ Plug-in 	
application/x-java-applet;version=1.6 	Java™ Plug-in 	
application/x-java-bean;version=1.6 	Java™ Plug-in 	
application/x-java-applet;version=1.7 	Java™ Plug-in 	
application/x-java-bean;version=1.7 	Java™ Plug-in 	
application/x-java-applet;jpi-version=1.7.0_15 	Java™ Plug-in 	
application/x-java-bean;jpi-version=1.7.0_15 	Java™ Plug-in 	
application/x-java-applet;deploy=10.15.2 	Java™ Plug-in 	
application/x-java-applet;javafx=2.2.7 	Java™ Plug-in 	
application/x-java-vm-npruntime 	Java™ Plug-in




It's just the same here:

 I've followed the steps from oracle and get the same results: it looks installed, it answers correctly to java -version, but I don't get Chromium to work with it. It just tells me that I should upddate the existing version (though they are already the last ones)



Java(TM) Télécharger les mises à jour de sécurité essentielles
Java plug-in for NPAPI-based browsers.
Nom :	Java Plug-in 1.7.0_25
Description :	Java plug-in for NPAPI-based browsers.
Version :	
Emplacement :	/usr/local/java/jre1.7.0_25/lib/i386/libnpjp2.so
Type :	NPAPI
 	 Désactiver
Types MIME :	
Type MIME	Description	Extensions de fichier
application/x-java-vm	Java™ Plug-in	
application/x-java-applet	Java™ Plug-in Applet	
application/x-java-bean	Java™ Plug-in JavaBeans	
application/x-java-applet;version=1.1	Java™ Plug-in	
application/x-java-bean;version=1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.1	Java™ Plug-in	
application/x-java-bean;version=1.1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.2	Java™ Plug-in	
application/x-java-bean;version=1.1.2	Java™ Plug-in	
application/x-java-applet;version=1.1.3	Java™ Plug-in	
application/x-java-bean;version=1.1.3	Java™ Plug-in	
application/x-java-applet;version=1.2	Java™ Plug-in	
application/x-java-bean;version=1.2	Java™ Plug-in	
application/x-java-applet;version=1.2.1	Java™ Plug-in	
application/x-java-bean;version=1.2.1	Java™ Plug-in	
application/x-java-applet;version=1.2.2	Java™ Plug-in	
application/x-java-bean;version=1.2.2	Java™ Plug-in	
application/x-java-applet;version=1.3	Java™ Plug-in	
application/x-java-bean;version=1.3	Java™ Plug-in	
application/x-java-applet;version=1.3.1	Java™ Plug-in	
application/x-java-bean;version=1.3.1	Java™ Plug-in	
application/x-java-applet;version=1.4	Java™ Plug-in	
application/x-java-bean;version=1.4	Java™ Plug-in	
application/x-java-applet;version=1.4.1	Java™ Plug-in	
application/x-java-bean;version=1.4.1	Java™ Plug-in	
application/x-java-applet;version=1.4.2	Java™ Plug-in	
application/x-java-bean;version=1.4.2	Java™ Plug-in	
application/x-java-applet;version=1.5	Java™ Plug-in	
application/x-java-bean;version=1.5	Java™ Plug-in	
application/x-java-applet;version=1.6	Java™ Plug-in	
application/x-java-bean;version=1.6	Java™ Plug-in	
application/x-java-applet;version=1.7	Java™ Plug-in	
application/x-java-bean;version=1.7	Java™ Plug-in	
application/x-java-applet;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-bean;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-applet;deploy=10.25.2	Java™ Plug-in	
application/x-java-applet;javafx=2.2.25	Java™ Plug-in	
application/x-java-vm-npruntime	Java™ Plug-in

---

### Post by amy4 on 2014-06-14
detailed steps to verify [[COLOR=#000000]Java installation and Java versions[/COLOR]]("http://tutorialswithexamples.com/how-to-verify-java-version/")

---

