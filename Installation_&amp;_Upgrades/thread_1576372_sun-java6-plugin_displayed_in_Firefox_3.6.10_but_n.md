---
title: "sun-java6-plugin displayed in Firefox 3.6.10 but not working"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by awagle on 2010-09-17
Initially when I upgraded to Lucid I uninstalled openJDK and switched back to sun-java5 packages due to some application support limitations.

Now I have to upgrade to sun-java6- packages. I removed the sun-java5 packages and installed the sun-java6 packages. Including the sun-java6-plugin.

I can see the plugin in about:plugins in Firefox 3.6.10 however nothing (like webex or applets) related to java works.

As a workaround I have used the Icedtea plugin which comes with open JDK and that seems to work. However I want to get the sun-java6-plugin working.

Any pointers?

---

### Post by lykeion on 2010-09-17
Maybe this: _[Choosing the default Java to use]("https://help.ubuntu.com/community/Java#Choosing%20the%20default%20Java%20to%20use")_

---

### Post by awagle on 2010-09-20
Thanks for the link but I have done that already. I don't have Open JDK installed so there is no switching required.

Either way java -version prints out the Sun JDK version.

I am hoping that the upgrade to 10.10 might solve it.

---

### Post by claracc on 2010-09-20
You can find some useful information in this link: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

---

### Post by awagle on 2010-09-20
Ok I found out the problem. Apparently Compiz had a problem displaying java applications with Java 5. I had used a workaround to export MToolkit as the default toolkit.

Removing that line from my /etc/environment solves this issue.

---

