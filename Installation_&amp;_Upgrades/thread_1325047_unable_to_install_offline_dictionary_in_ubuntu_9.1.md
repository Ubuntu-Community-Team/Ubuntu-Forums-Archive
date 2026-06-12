---
title: "unable to install offline dictionary in ubuntu 9.10"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by bilol on 2009-11-13
Dear all,
I was unable to install offline dictionary in ubuntu 9.10
I performed the following steps in order to do this:
(1) sudo apt-get install dictd 
    sudo apt-get install dict-gcide 
    sudo apt-get install dict-moby-thesaurus 
(2) Go to Application>Office>Dictionary> open the dictionary
(3) Edit>(right click)Preference>Source>Add>
(4) Now enter the following:
    Description: Local Dictionary
    Transport: <Unchanged>
    Hostname:  localhost
    Port: <unchanged>
(5) Add>Source>Local Dictionary(select)>Close

Next time when I open the dictionary and search for a word definition, it gives the following error:
[B]Error while looking up definition
Connection failed to the dictionary server at localhost:2628[/B]

Any help will be appreciated......

---

### Post by bilol on 2009-11-16
Can anybody help me out of this problem?

---

### Post by bilol on 2009-11-20
I have installed "artha" and it is working fine.

---

### Post by xiaoyong on 2009-11-25
use 127.0.0.1 as hostname instead of using localhost.

---

### Post by reddox on 2009-11-26
127.0.0.1 fixed the problem for me.

---

