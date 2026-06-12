---
title: "umlaute problem"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by shizow on 2005-06-28
i have hoary and use english as the  language
but i need the see german umlaute correct
for example if i write something in xemacs with umlaute
save it and make a less i see strange symbols
or when i read my mails with mutt

my locale gives
~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=


i installed the following languages with
dpkg-reconfigure locales

de_DE.UTF-8 
de_DE.UTF-8@euro                                                                          
de_DE@euro                                                                                
en_US                                              
en_US.UTF-8 

and set the default language to en_US.UTF-8

when i set the default language to de_DE@euro the umlaute are displayed correct,
but i dont want that because then all the programs like firefox use german language in their menus etc

---

### Post by emmet on 2005-06-28
Does this help?

[http://lists.gnu.org/archive/html/help-gnu-emacs/2003-08/msg00393.html](http://lists.gnu.org/archive/html/help-gnu-emacs/2003-08/msg00393.html)

---

### Post by shizow on 2005-06-29
the problem is not only emacs but programms like mutt too

---

### Post by shizow on 2005-07-08
can anyone help?

---

