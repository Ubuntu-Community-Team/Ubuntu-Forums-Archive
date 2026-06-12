---
title: "Firefox Java Plugin Not Working - Blank Area Where Java Applet Should Be"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by jon_herr on 2007-05-18
When I perform a "about:plugins" I get this (see below)

But java applets on web pages are blank... nothing to be seen... I've re-installed, re-linked, etc.  What am I doing wrong?  

Thanks,
Jon

Java(TM) Plug-in 1.5.0_05-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_05

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_05 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_05 	Java 		Yes

---

### Post by taurus on 2007-05-18
If you can list the site here, perhaps somebody can check it out for you.

---

### Post by BUGabundo on 2007-05-18
I have the same problem with swiftfox... how can I link the FF plugins for it?

---

### Post by mpvano on 2007-05-18
Do you have java and javascript enabled in the browser preferences - BOTH must be enabled for java to work.

Also note that if you use "NoScript", the site in question must have javascript allowed as well.

Java won't work without javascript because javascript is what launches the applet.

hope it's this simple...

Mario

---

### Post by mcdragon on 2008-05-18
I have the same problem and I have Java and JavaScript activated in Firefox.

Actually removing the icedtea package through Synaptics did the trick.

---

