---
title: "Cannot update Eclipse"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by valmar on 2010-03-15
Dear All,

      I installed the Eclipse IDE using Ubuntu packages. (Version 3.5.1. Package name:eclipse).

A few days back, version 3.5.2 was released. I would like to update, so I added the following websites to the list of available ones:

[http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo)
[http://download.eclipse.org/eclipse/updates/3.5](http://download.eclipse.org/eclipse/updates/3.5)

I then tried with Check for Updates. While on my Mac installation this results in an update to 3.5.2, on Ubuntu the program says there is nothing to update.

If I try to install manually, choosing Install New Software and the then selecting the Eclipse Platform 3.5.2, I get the following error:

Cannot complete the install because of a conflicting dependency.
  Software being installed: Eclipse Platform 3.5.2.M20100211-1343 (org.eclipse.platform.ide 3.5.2.M20100211-1343)
  Software currently installed: Eclipse Platform 3.5.1 (Eclipse Platform 3.5.1)
  Only one of the following can be installed at once: 
    Equinox Provisioning Metadata Generator 1.0.101.R35x_20100114 (org.eclipse.equinox.p2.metadata.generator 1.0.101.R35x_20100114)
    Equinox Provisioning Metadata Generator 1.0.100.v20090520-1905 (org.eclipse.equinox.p2.metadata.generator 1.0.100.v20090520-1905)
  Cannot satisfy dependency:
    From: Eclipse Platform 3.5.1 (Eclipse Platform 3.5.1)
    To: org.eclipse.equinox.p2.metadata.generator [1.0.100.v20090520-1905]
  Cannot satisfy dependency:
    From: Equinox p2 Provisioning 1.1.2.R35x_v20091106-7u6FbQFUAtsCKD5Fxz0qz0fb2932 (org.eclipse.equinox.p2.user.ui.feature.group 1.1.2.R35x_v20091106-7u6FbQFUAtsCKD5Fxz0qz0fb2932)
    To: org.eclipse.equinox.p2.metadata.generator [1.0.101.R35x_20100114]
  Cannot satisfy dependency:
    From: Eclipse Platform 3.5.2.M20100211-1343 (org.eclipse.platform.ide 3.5.2.M20100211-1343)
    To: org.eclipse.equinox.p2.user.ui.feature.group [1.1.2.R35x_v20091106-7u6FbQFUAtsCKD5Fxz0qz0fb2932]

does anyone know if it is possible to update the packaged verison of Eclipse or if I should install the binary from the website?

Thank you very much for your help

    Valerio

---

### Post by bruno9779 on 2010-03-15
You previous install of eclipse conflicts with the 3.5.2.

remove 3.5.1 and try again.

---

### Post by valmar on 2010-03-15
Ehm... I don't understand. The packages for 3.5.2 are not in the repositories, as far as I know. What I am trying to do is install the latest in the repositories (3.5.1), and then try to update from within Eclipse. How can I remove the previous installation

Thanks for the quick answer

    Valerio

---

### Post by k23 on 2010-03-15
I ended up with clean custom Eclipse installation downloaded from their site. I think there is a bug in Ubuntu preventing update sites in Eclipse to work properly. Now I can have PDT, Aptana, PyDev installed without problem.

---

