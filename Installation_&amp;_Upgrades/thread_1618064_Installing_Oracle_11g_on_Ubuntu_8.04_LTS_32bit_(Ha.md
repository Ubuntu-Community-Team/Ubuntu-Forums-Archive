---
title: "Installing Oracle 11g on Ubuntu 8.04 LTS 32bit (Hardy Heron)"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by hp.bhathiya on 2010-11-10
I have been following [this]("http://www.pythian.com/news/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron/") tutorial. I used exact same Ubuntu version and Oracle 11g (chcksum and MD5 verified)Everything went alright up to the final stage of starting up the setup. when the setup attempt to run it get me following error
```
Exception in thread “main” java.lang.NoClassDefFoundError
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Class.java:164)
at java.awt.Toolkit$2.run(Toolkit.java:821)
at java.security.AccessController.doPrivileged(Native Method)
at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
at com.jgoodies.looks.LookUtils.isLowResolution(Unknown Source)
at com.jgoodies.looks.LookUtils.(Unknown Source)
at com.jgoodies.looks.plastic.PlasticLookAndFeel.(PlasticLookAndFeel.java:122)
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Class.java:242)
at javax.swing.SwingUtilities.loadSystemClass(SwingUtilities.java:1783)
at javax.swing.UIManager.setLookAndFeel(UIManager.java:480)
at oracle.install.commons.util.Application.startup(Application.java:758)
at oracle.install.commons.flow.FlowApplication.startup(FlowApplication.java:164)
at oracle.install.commons.flow.FlowApplication.startup(FlowApplication.java:181)
at oracle.install.commons.base.driver.common.Installer.startup(Installer.java:265)
at oracle.install.ivw.db.driver.DBInstaller.startup(DBInstaller.java:114)
at oracle.install.ivw.db.driver.DBInstaller.main(DBInstaller.java:132)
```

i gone though this same procedure on brand new ubuntu installations three times but still getting this error.
for all this operation I'm using Oracle Virtual Box.

Any helpful tips?

---

### Post by manojankk on 2011-12-03
This article clearly describes installation of Oracle 11g release 2 on Ubuntu desktop (Posted on 03-December-2011)
[http://sqlandplsql.blogspot.com/2011/12/installing-oracle-11g-on-ubuntu.html](http://sqlandplsql.blogspot.com/2011/12/installing-oracle-11g-on-ubuntu.html)

Steps are same for 8.04. I recommend you to upgrade to 10.04 since it is a long term support version before trying Oracle. good luck !

---

