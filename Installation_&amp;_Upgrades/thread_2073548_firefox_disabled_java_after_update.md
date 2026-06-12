---
title: "firefox disabled java after update"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by oxman on 2012-10-19
12.04, current security updates, life was good. Did an update that  included a firefox update. Java is turned off in firefox and I have been trying  to get it going again. I'm using OpenJDK 7.
Any help is appreciated.

---

### Post by oxman on 2012-10-22
Any help is appreciated.

---

### Post by efflandt on 2012-10-22
Did you always have openjdk-7, or did you have openjdk-6 and recently switched to openjdk-7 (including icedtea-7-plugin)?

I recently completely removed everything related to openjdk-6 (including icedtea) and installed openjdk-7 because 1 of many mods in a game server required Java 7.  Until you mentioned it I did not notice that firefox plugins did not mention Java.  I installed **icedtea-7-plugin**  (using Synaptic) and now **IcedTea-WEB Plugin** to execute Java applets shows up in Firefox 16.0.1 plugins and is not disabled.  Although, I do not know a website that uses Java to test it on.

---

