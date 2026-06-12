---
title: "Unable to save in www/apache2-deafult"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by hormonx on 2007-07-07
I just installed LAMP on Feisty 7.04 but there is a little problem, i am unable to save or create folders in the www folder.  i know this has something to do with permitions but how do i give myself permitions to the folder not having ability to log in as a root?

Any help would be appreciated.

HX

---

### Post by reclusivemonkey on 2007-07-08
> **hormonx said:**
> I just installed LAMP on Feisty 7.04 but there is a little problem, i am unable to save or create folders in the www folder.  i know this has something to do with permitions but how do i give myself permitions to the folder not having ability to log in as a root?


Using sudo will allow you to execute commands as root. You can then either change the permissions, or add your user to the relevant group.

---

