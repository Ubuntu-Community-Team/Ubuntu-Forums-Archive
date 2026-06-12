---
title: "pear installation"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by jural on 2006-08-14
Hello, I'm having problems with pear installation. I've been browsing these forms and google for the past few hours and comming up with dead ends. Seems like a few people have had the same issue, but all the posts end with "I've fixed it!" and noboday actually posting the fix.

php says PEAR is installed @ /usr/share/pear , but no such directory exsists. I get no errors on istallation of pear. Any help would be great.

Thanks in advance.

---

### Post by thoolihan on 2006-09-23
it's installed in /usr/share/php

If you install say SOAP, by doing
#pear install --alldeps SOAP

The directory that shows up will be /usr/share/php/SOAP

php puts /usr/share/pear in the path, so you'll want to add /usr/share/php to your php include path.

---

