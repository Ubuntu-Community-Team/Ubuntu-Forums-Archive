---
title: "Apache2 - Is not working at all!"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by superstar on 2007-10-07
Hello everyone!

I've tried to install Apache2 into my computer and nothing, is not working.

Then I followed this tutorial ( [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) ) stil nothing.
I don't know what is wrong with it.

A had two folders in /etc  i thougt there are 2 versions of apache. one was "apache" the oder one was apache2. i tried to remove with "sudo aptitude remove apache."
then i identified where apache was ( "whereis apache") and i deleted manually the folder so just apache2 will remain in to my pc, but stiil nothing.

I am running Xubuntu.

If anyone can help me please reply!

Thanks.

---

### Post by Mr.Ganja on 2007-10-09
if you go in your browser to 127.0.0.1, does it show anything like "Index of /" and shows the contents of /var/www on your computer? Does the apache2 process even appear in  the process list? Does the apache process show up too? It should be gone. What was the output of the sudo-apt remove apache?

---

