---
title: "Setting domain name"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by starNIX on 2005-07-25
How the heck do I set the domain name of my PC?  In gentoo it was in /etc/dnsdomainname.  In Ubuntu this doesnt work.  Right now mine is set at localdomain.  I want to change it to the-hollow.net.  Any advice?

---

### Post by heimo on 2005-07-25
Change it in /etc/hosts and check the result using dnsdomainname (on command line, no flags).

---

### Post by starNIX on 2005-07-27
This is what i have in my hosts file and it still displays"

localdomain

when I run dnsdomainname

localhost.localdomain localhost ubuntubox ubuntubox.the-hollow.net

Am I doing something wrong?

---

### Post by heimo on 2005-07-27
[QUOTE=starNIX]This is what i have in my hosts file and it still displays"

localdomain

when I run dnsdomainname

localhost.localdomain localhost ubuntubox ubuntubox.the-hollow.net

Am I doing something wrong?[/QUOTE]

Try:
 ```
ubuntubox.the-hollow.net ubuntubox localhost.localdomain localhost 
```

---

