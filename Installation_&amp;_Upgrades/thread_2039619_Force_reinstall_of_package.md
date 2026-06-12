---
title: "Force reinstall of package"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by hornetster on 2012-08-09
Have searched for this and can't find a solution...
Believe I have screwed my Apache and/or Zoneminder packages, and have looked for a method to force a 'reinstall' of a package (don't want to have to uninstall/reinstall - scared it could get ugly..) but can't find one.
How do I fix a broken package?
Thanks.

---

### Post by unevenflow on 2012-08-09
Hey you could try

**sudo apt-get install --no-install-recommends package_name**

---

### Post by hornetster on 2012-08-25
> **unevenflow said:**
> Hey you could try

**sudo apt-get install --no-install-recommends package_name**

Nope, just get "<package-name> is already the newest version."

---

### Post by dino99 on 2012-08-25
choices:

sudo apt-get install --reinstall mypackage

sudo dpkg-reconfigure mypackage

( or if the other solutions have failed: 

sudo apt-get purge mypackage && sudo apt-get install mypackage

and logout/in )

---

### Post by hornetster on 2013-01-11
a belated thanks!

---

### Post by Nirgali on 2013-02-26
posted on wrong topic, my bad.

---

