---
title: "Eclipse 3.3 / Ubuntu / Cant find junit, jaxme, log4j"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by ture_atlantis on 2007-11-15
So i was having difficulties installing myeclipse with Ubuntu's version of Eclipse (3.2), so i manually installed Eclipse 3.3 and have added MyEclipse.

After the update, my projects have massive amounts of errors due to the fact that eclipse cannot find/see common libraries like junit, jaxme, and log4j. They are all in the same place '/usr/share/java' and i feel like this directory should be part of a default classpath.

Is there a way for eclipse/java in general to know that most libraries are in /usr/share/java? If not, how did Ubuntus version of eclipse not generate the same errors, and knew where these libraries were?

Thanks.

---

### Post by thomasalbright on 2008-02-29
You may not have the correct Java package.  You need the Sun packages, not java-common.  Look at [http://portal.chrost.com/index.php?option=com_content&task=view&id=5&Itemid=17](http://portal.chrost.com/index.php?option=com_content&task=view&id=5&Itemid=17), it may help.

---

