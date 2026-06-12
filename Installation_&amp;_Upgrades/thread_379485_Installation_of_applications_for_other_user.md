---
title: "Installation of applications for other user"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by geezerone on 2007-03-08
Hi

If I wanted to install, for example, Java or Adobe for a user with 'users' group access how would you provide temporary rights for this? I see that you can run a program as root or other level but what would you put in the 'box' and what do the login shell and preserve environment mean?

TIA

---

### Post by zvacet on 2007-03-09
You install as root,but other users can work with that programs,because only thing they can not do is adminster system.If programs ask for sudo they can not work with this type of program,because they can not use sudo.

---

