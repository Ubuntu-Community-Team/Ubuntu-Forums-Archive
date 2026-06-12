---
title: "python-pandas installation problem"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by tomasz74 on 2012-09-11
Hello 

Does anyone know why python-pandas package is not available?

[FONT="Courier New"]~$ sudo apt-get install python-pandas
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-pandas[/FONT]

What is the best solution to install it in Ubuntu 10.04?

---

### Post by tomasz74 on 2012-09-11
Ok. Found sort of answer. 

pandas require numpy 1.6, where by default in Ubuntu 10.4 is 1.3

To install newer version of numpy:

[http://ubuntuforums.org/showthread.php?t=1573925](http://ubuntuforums.org/showthread.php?t=1573925)

After 
[FONT="Courier New"]sudo easy_install pandas[/FONT] should work

---

