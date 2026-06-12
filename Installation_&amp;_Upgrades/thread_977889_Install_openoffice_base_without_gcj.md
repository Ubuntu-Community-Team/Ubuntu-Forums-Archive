---
title: "Install openoffice base without gcj"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by MarilenCorciovei on 2008-11-10
Hello, 

I am trying to install openoffice.org-base yet even if I installed sun-jdk it still wants to install a bunch of gcj related packages. Is there any way to install openoffice.org-base without all the gcj part in intrepid?

bsh bsh-gcj gcj-4.3-base libgcj-bc libgcj-common libgcj9-0 libgcj9-jar
  libjaxp1.3-java libjaxp1.3-java-gcj libjline-java libxalan2-java
  libxalan2-java-gcj libxerces2-java libxerces2-java-gcj

As far as I can tell none of these are really needed.

Thank you for your help,
Len

---

### Post by MarilenCorciovei on 2008-11-17
Finally I managed [to install the package]("http://www.len.ro/2008/11/openofficeorg-base-on-intrepid/") without the gcj part by doing an apt-get with -d option just to download the packages and then manually installing the packages with dpkg (without the gcj ones)

---

