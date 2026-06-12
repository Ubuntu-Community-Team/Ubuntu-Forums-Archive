---
title: "unable to update java 6 for mozilla and chromium"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by eshkaml on 2012-09-18
Hi, I am trying to open a GUI which needs at least Java 6. When I am trying to download JAVA a file called gui.jnlp is coming. I am saving this file, and after opening it it is showing Errors.Please Help.I am attaching screen shot of errors sequentially.

---

### Post by black veils on 2012-09-18
if you have no java installed, go to software center, search "openjdk" and install the java 6 runtime.

if it doesnt show as a result, you may need to enable the canonical partners repository or install the medibuntu repository.

---

### Post by black veils on 2012-09-18
(oops sorry, posted in the wrong thread!)

---

### Post by QIII on 2012-09-18
Don't install OpenJDK 6 or Oracle Java 6.  They are both vulnerable to attack and are due to reach end of life in November 2012.

Install OpenJDK 7 and see if it works.  It doesn't always work because some developers of both applications and web applets don't seem to realize or care that it is the open source reference implementation for Oracle Java 7.  The applet launcher xml in the web page may be looking specifically for Oracle Java 7.

If OpenJDK does not work, look in the Java wiki in my signature under the Oracle Java 7 section, "Command line methods" and find the link "Using webupd8.org's strikingly simple method" to install Oracle Java 7.

---

