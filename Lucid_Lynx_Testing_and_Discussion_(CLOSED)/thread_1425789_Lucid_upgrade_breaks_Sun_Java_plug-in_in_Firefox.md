---
title: "Lucid upgrade breaks Sun Java plug-in in Firefox"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ktraub on 2010-03-09
Hi All,

Looks like my Sun Java plug-in under Firefox is broken after an upgrade to Lucid (alpha3)
I've tried uninstalling the plug-in and Java, both from the repositories, several times, but no joy.
Launching any browser based applets just act like there's no plug-in installed.

The plug-in works fine in google chrome on the same lucid machine.

Has anyone else seen this?

---

### Post by CoreyB. on 2010-03-09
sun java was removed from the main repos in Ubuntu starting with Lucid.  It has been moved to the partner repository.  You could try installing sun java from there or maybe [icedtea6-plugin]("http://packages.ubuntu.com/lucid/icedtea6-plugin") would work.

---

### Post by ktraub on 2010-03-09
CoreyB. I was installing the Sun Java plugin from the partner repo.
But [icedtea6-plugin]("http://packages.ubuntu.com/lucid/icedtea6-plugin") did the trick.

Thanks much!:D

---

### Post by Uncle Spellbinder on 2010-03-10
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-) - 32 Bit

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-) - 64 Bit

Works perfectly in Lucid. Java current version.

---

### Post by emarkay on 2010-03-21
See this thread for Java issues:
[http://ubuntuforums.org/showthread.php?p=9004764](http://ubuntuforums.org/showthread.php?p=9004764)

---

### Post by jms-ubuntu-en on 2010-03-23
> **Uncle Spellbinder said:**
> 
Works perfectly in Lucid. Java current version.
Thanks, firefox java plugin works now in 64-bit version

---

### Post by Uncle Spellbinder on 2010-03-23
> **Uncle Spellbinder said:**
> [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-) - 32 Bit

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-) - 64 Bit

Works perfectly in Lucid. Java current version.[QUOTE=jms-ubuntu-en;9013751]Thanks, firefox java plugin works now in 64-bit version
[/QUOTE]

You're welcome. One of the best, tutorials I can recall. Clear, concise, easy to follow.

---

### Post by jelevin on 2010-04-13
Thanks.  This fixed lucid + java for me.

---

### Post by PRC09 on 2010-04-13
For plugin not recognized after install see here.......

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/532174](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/532174)

---

### Post by justleen on 2010-04-26
For the people who find this thread:
Upgrading to 10.04 broke ilo remote console, which needs jre and a plugin. In my case it was fixed with installing the following packages: openjdk-6-jre  icedtea6-plugin

---

