---
title: "Java not at all working"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Mets on 2008-06-09
Hi,

I can't seem to get Java or Java plugins for browsers working.  I have 8.04, and I installed sun-java6-bin and sun-java6-jre.  Java applications worked fine, so I tried to install gcjwebplugin through Firefox.  That didn't load applets, so I tried the icedtea version.  That only showed a big gray box instead of the applet.  I uninstalled them, but now no Java applications work, including the original ones I tested before the plugins.

I tried installing ubuntu-restricted-extras, but that didn't fix anything - web applets don't work, and applications don't work.

Can somebody help me fix this?

---

### Post by Mets on 2008-06-09
Ok, I used Synaptic to completely remove openJDK from my system, and now all of the applications work fine again.  This still leaves me without a working plugin in firefox though.

I did some Googling, and I saw some older posts (2007) that said there was no plugin for x86_64.  When I run java -version I get

```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)
```

When I try to install the plugin, I get
```
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```


I installed with Wubi, and I don't recall even having an option for 64-bit.  Could this be the problem?

---

