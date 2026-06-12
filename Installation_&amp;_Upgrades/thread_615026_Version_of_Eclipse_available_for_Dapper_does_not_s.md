---
title: "Version of Eclipse available for Dapper does not support Android"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Skilly on 2007-11-16
Google specify Eclipse versions 3.2 or 3.3 (Europa) as a requirement for installing the Android SDK. Via apt repositories, the version of Eclipse that is available for Dapper is 3.1. I am still running Dapper as I made the gamble early on on  staying with a LTS version, not realising the hassle that I would have going forward with trying to gain access to new functionality. In a nutshell, can I upgrade Eclipse on my dapper machine to version 3.2 and if so, how?

---

### Post by nicko7i on 2007-11-18
Eclipse is "pure java", so you should be able to download Europa from eclipse.org.

You'll need a jvm that works with Eclipse.  If Dapper has the  sun-java5-jdk package, that's one possibility.  You'll need to check if Android works with Java5 or not.

---

### Post by Skilly on 2007-11-19
Thanks Niko7i! I can confirm that I've downloaded version 3.2 from eclipse's site and it works fine in Dapper

---

