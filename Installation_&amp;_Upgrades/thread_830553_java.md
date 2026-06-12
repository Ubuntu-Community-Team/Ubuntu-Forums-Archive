---
title: "java"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by fboxall on 2008-06-15
I have ubuntu within Windows XP Pro, with Java on the windows side so I can work Washington Post crosswords.  When I tried crossword with ubuntu WP said "you need Java".  So I went to ubuntu add/remove - no java.  So I went to synaptic package manager, did update, and downloaded java into unbuntu.  Now I do not get message from WP but I still cannot work crossword.  I hope someone can tell me how I might get Java to work.

---

### Post by powerpleb on 2008-06-15
If you have 32bit Ubuntu you can install the Sun JRE and Sun Java Runtime in Add/Remove Applications. Also uninstall OpenJDK and Icedtea. You will probably need to open System > Software Sources and enable the restricted and multiverse repositories.

If Ubuntu is 64bit I don't think you can fix it... yet.

---

### Post by Sef on 2008-06-16
> So I went to ubuntu add/remove - no java

In add/remove, you need to change show from the default to 'All Available Applications'.

> If Ubuntu is 64bit I don't think you can fix it... yet. 

For 64-bit Ubuntu, download OpenJDK, it works on almost all websites.  There are a few where java is needed.  See my link below for more information.

---

### Post by fboxall on 2008-06-17
to Ubuntu Mater Roasteer: I did as yoou suggested and it worked.  Many thanks.

---

