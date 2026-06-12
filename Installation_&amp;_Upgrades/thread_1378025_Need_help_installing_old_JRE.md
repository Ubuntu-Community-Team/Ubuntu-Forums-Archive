---
title: "Need help installing old JRE"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by HectorG on 2010-01-10
Anyone know how I can install an old version of java  jre? I am looking for version 1.5 specifically, reason being I have an old Cisco router that needs it to run the configuration GUI (SDM) correctly.

---

### Post by Mighty_Joe on 2010-01-11
[download it]("http://java.sun.com/products/archive/j2se/5.0_21/index.html") and [follow the instructions]("http://java.sun.com/j2se/1.5.0/jre/install-linux.html").

---

### Post by HectorG on 2010-01-13
I tried doing that but it doesn't show up for some reason. I checked in the control panel and all I see is the new version of it.

---

### Post by Mighty_Joe on 2010-01-14
What do you mean "show up"?  Since you are bypassing the Ubuntu repository, you have to set up the environment (i.e. PATH, JAVA_HOME) yourself.  [These instructions]("http://sites.google.com/site/easylinuxtipsproject/java") are for the current version of Java, but will give you a good idea as to how to fully integrate a manually installed version of Java with Ubuntu, if that's what you want.

---

### Post by HectorG on 2010-01-14
Mighty_Joe you are mighty indeed! It worked like a charm with that last link you gave me. I had installed it prior to reading it  but never set the paths or plugin in firefox. Anyway thanks for the help!:popcorn:

---

### Post by Mighty_Joe on 2010-01-15
[IMG]http://www.coderanch.com//images/smilies/jr-beerchug.gif[/IMG]

---

