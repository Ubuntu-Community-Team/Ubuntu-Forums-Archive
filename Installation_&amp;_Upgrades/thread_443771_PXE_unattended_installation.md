---
title: "PXE unattended installation?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2007-05-14
Hi,
I have successfully setuped PXE deployment for ubuntu desktop 7.04.
I want to know are there anyway to deploy ubuntu unattended?
I used to setup CentOS & Fedora unattended with a ks.cfg file


My Deployment Server:
Windows 2003 Enterprise SP2
Windows Deployment Service(WDS or RIS) + IIS6

Sincerely,
Reece M

---

### Post by RealMurphy on 2007-06-08
Hi,

I've just seen this thread, sorry for being late

AFAIK ubuntu can be installed automatically via PXE if you use the great FAI package (use 'apt-cache search ^fai' to see which packages are available, they are in the universe repo).

HTH

Carsten

---

