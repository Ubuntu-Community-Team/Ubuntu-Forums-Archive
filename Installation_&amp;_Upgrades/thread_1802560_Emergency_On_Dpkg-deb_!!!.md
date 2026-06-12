---
title: "Emergency On Dpkg-deb !!!"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by hieuhoang on 2011-07-12
Hi everyone,

I am beginner of dpkg-deb ! I have just used **dpkg-deb** tool to make an installer for Ubuntu. After installing , the target folder in /usr/lib/... at the terminal , it run very well ! But I started to run from Applications\Accessories\ ... failed . I have also tried to search but without luck . Who knows the problem , pls help me ! many thanks in advance.

---

### Post by raja.genupula on 2011-07-12
dpkg --get-selections | grep install deb_name 


check is it properly installed or not by that .  

type that deb_name in terminal  to invoke that program .

---

