---
title: "Upgrade 10.10 -&gt; 11.04 fails An unresolvable problem occurred while calculating the u"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by pki on 2011-06-19
Hi

I am getting this problem upgrading from 10.10 to 11.04.

```
An unresolvable problem occurred while calculating the upgrade:
E:B&#322;&#261;d, pkgProblemResolver::Resolve zwróci&#322; b&#322;&#261;d, mo&#380;e to by&#263; spowodowane zatrzymanymi pakietami.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

Je&#347;li &#380;aden nie dotyczy, to prosz&#281; zg&#322;osi&#263; b&#322;&#261;d pakietu "update-manager" i zawrze&#263; w raporcie pliki z /var/log/dist-upgrade/.

```

I have attached the logs

I also have created a bug, but up to now it is unanswerded. [https://bugs.launchpad.net/update-manager/+bug/797291](https://bugs.launchpad.net/update-manager/+bug/797291)

Would you like to help?

---

### Post by jerrrys on 2011-06-20
have you unchecked all third party sources in 'software sources'?

---

### Post by pki on 2011-06-20
Yes I have unchecked ALL third party sources.

---

### Post by pki on 2011-07-02
Bump?
No one likes to help?

---

### Post by Olph on 2011-07-06
I have the same issue on my parent's computer (almost a clone of my own computer, with which I have had no issues).

Prior to the "unresolvable problem" message, I get a message that the installation has unchecked third party sources.

---

### Post by pki on 2011-07-06
I have solved this problem now.

Go to the software center, go to installed software, click other and uninstall ALL packages there. I have also uninstalled Xserver and xorg. The done the upgrade from console and installed X again from aptitude.

---

