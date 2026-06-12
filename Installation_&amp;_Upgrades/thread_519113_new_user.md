---
title: "new user"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by winlinfix on 2007-08-06
HI,

i am new in ubuntu...

i understand ubuntu bit. 
apt-get install packagename

sometime package name are different in ubuntu so how to find them?
how to use apt-get cache?

is there any example

if i am searching for php

Thank you

---

### Post by Pumalite on 2007-08-06
Why don't you try System>Administration>Synaptic Package Manager>Search? It's easier.

---

### Post by tbfr on 2007-08-06
Using synaptic, the graphical frontend to apt, is indeed the easiest solution, here is a guide:
[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")

But to answer your question, to search for php related packages just type:

apt-cache search php

Since there are a lot of php related packages in Ubuntu, you can also write 'apt-cache search php | more'. This will only show you one page at a time. Hit space to get to the next page.

If you need a specific php module you can also filter the results. For example, if you search for the PHP MySQL extension you can type:

apt-cache search php | grep mysql

---

### Post by winlinfix on 2007-08-06
HI,

apt-get search php really help.. thanks for that

1)i would like to use GUI for ubuntu for users so they can access xls sheet files and doc files and secure crt and all application.

2)i would like to use ubuntu on server for webserver with cpanel or webmin
so i would like to know which cd shall i download and install for server and user level ?

how can i get more help in console..


Thank you,

---

### Post by Pumalite on 2007-08-06
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

---

