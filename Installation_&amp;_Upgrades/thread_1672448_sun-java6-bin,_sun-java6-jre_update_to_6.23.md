---
title: "sun-java6-bin, sun-java6-jre update to 6.23?"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by emiller12345 on 2011-01-20
I noticed that the [http://archive.canonical.com](http://archive.canonical.com) lucid partner repository which contains the sun/java6 version is out of date, being the 6.22 version.  Does anyone know if this will be updated to the 6.23 version? I've been having trouble trying to install some apps that require java, and I suspect that it might be a version issue.  I prefer to install through the package manager cause the direct .bin install is not as nice.  Thank you

---

### Post by lykeion on 2011-01-21
According to Oracle: "Java SE 6u23 does not contain any additional fixes for security vulnerabilities to its previous release, Java SE 6u22. Users who have Java SE 6u22 have the latest security fixes and do not need to upgrade to this release to be current on security fixes."

You can test your Java version here: [http://www.javatester.org/version.html](http://www.javatester.org/version.html)

What problems are you having and what apps? It's unlikely a version issue.

---

### Post by emiller12345 on 2011-01-23
Okay, yeah, I wasn't sure. I was trying to play around with jmonkeyengine and it was throwing errors.  I followed the installation tutorial and its working now.  I was getting an Error involving sun.misc.Base64Decoder(), but it turns out it's not really an error and will still compile. I was thinking that the class was in the new release, but not in the older one. Jmonkeyenginge works well though.

---

