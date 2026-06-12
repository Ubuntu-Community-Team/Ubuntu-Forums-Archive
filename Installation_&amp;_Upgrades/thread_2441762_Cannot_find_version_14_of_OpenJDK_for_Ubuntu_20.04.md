---
title: "Cannot find version 14 of OpenJDK for Ubuntu 20.04"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by adam-przedniczek on 2020-04-26
I've installed Ubuntu 20.04 Focal Fossa and was trying to install the latest Java JDKs in both flavours: OpenJDK and Oracle.
However, searching via **apt search** gives **OpenJDK** (and also JRE) only up to **11th** edition.

Searching on **[https://packages.ubuntu.com/](https://packages.ubuntu.com/)** narrowed do **focal** distribution also gives results up to openjdk-**11**-jXX.
Switching the distribution of choice to **eoan**, gives all up to date versions including **14**th.

I'm not asking how to enforce the installation of exactly 14th edition of OpenJDK, but rather I'm asking for the reason for this.
Is it due to any security reasons and I should also get rid of 14th Oracle version (downgrade it to 11th)?
Or just patiently wait because OpenJDK-14 need to be approved for Focal Fossa?

-------
**THE PROBLEM WAS SOLVED BY ITSELF: Today I've noticed that OpenJDK-14 is finally added to Ubuntu 20.04 standard repositories.**

---

