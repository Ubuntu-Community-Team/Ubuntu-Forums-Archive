---
title: "Firefox 3.6 and java"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by bako on 2010-01-30
Hi all.
i update the ff at the version 3.6. I proceeded in this way:
- remove all the old firefox via apt.
- download the package from mozilla website.
- unpack the tar.gz in /opt/firefox

now, i try to use a java applet but the java is not recognize.
ff said that i had to download the jre, but it is already present
```
stefano@stefano-desktop:~$ whereis java
java: /usr/bin/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz

```

i installed the java and java plugins but nothing.

in the list of addons there isn't the java addons.

any idea?

---

### Post by kc1di on 2010-01-30
Hi ,
Java normally resides in /usr/lib/jvm

---

### Post by Kimm on 2010-01-30
Are you running Ubuntu 32bit or 64bit?

If you are running the 64bit version of Ubuntu, you cant use the bundled 64bit JRE with a 32bit version of firefox (as the one provided from the Firefox website). So, you'll have to install the 32bit Java-package: ia32-sun-java6-bin

---

### Post by kansasnoob on 2010-01-30
Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727)

The "fix" is described here:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

---

