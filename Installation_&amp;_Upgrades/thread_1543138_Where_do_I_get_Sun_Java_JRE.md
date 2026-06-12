---
title: "Where do I get Sun Java JRE?"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2010-07-31
I tried to install the Openfire deb package but it complains that it cannot install sun-java6-jre. The Ubuntu help ([https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)) says that it's in the "multiverse" and I need to enable it in my apt sources. Afaict, it is already enabled. Here's the file without the comments:

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

I can't find that JRE package in apt-get and in Synaptic. Where do I get it from? Will another package do, too?

---

### Post by howefield on 2010-07-31
In Synaptic, choose Repositories from the Settings menu, then enable the partner repositrory from the Other Software tab.


Reload and you'll find sun-java6-jre

You might also want sun-java6-plugin.

---

### Post by ygoe on 2010-07-31
> **howefield said:**
> In Synaptic, choose Repositories from the Settings menu, then enable the partner repositrory from the Other Software tab.

Reload and you'll find sun-java6-jre

It's still not there. :(

---

### Post by howefield on 2010-07-31
> **LonelyPixel said:**
> It's still not there. :(

Err... yes it is :)

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun) Java moved to the Partner repository

> Sun Java moved to the Partner repository

For Ubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the Ubuntu archive. It is recommended that you use openjdk-6 instead. 

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line: 
     add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

---

### Post by ygoe on 2010-07-31
I see. The proposed source was:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

The correct source is:

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Now it's here, too.

---

