---
title: "More Openoffice problems in Edgy: track changes crashes"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by zilverling on 2006-10-28
Apart from the font rendering I now find that OpenOffice 2.04 in Edgy crashes systematically when I work with tracking editorial changes and want to accept or reject changes.

Is it possible to revert to a previous version of OpenOffice within Edgy? If so, how?

---

### Post by okl on 2006-10-28
There is a way to get it all working within edgy but it's a little bit difficult.
1.) first you have to use apt-get or whatever you use to get rid of all openoffice.org packages.
2.) add the following line to your /etc/apt/sources.list:
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse universe
3.) comment out the following line in your /etc/apt/sources.list:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
4.) sudo apt-get update
5.) install openoffice.org Version 2.02 from the dapper source.
6.) get the deb-file of libfreetype6 from a dapper-web-source
7.) sudo dpkg --install libfreetype6_2.1.10-1ubuntu2.1_i386.deb
8.) copy /usr/lib/libfreetype.so.6.3.8 to /usr/local/lib/
9.) delete the dapper line from /etc/apt/sources.list and uncomment the edgy line again.
10.) sudo apt-get update
11.) sudo apt-install libfreetype6 will install the edgy version of libfreetype6 again.
12.) open a terminal and enter:
export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8
oowriter

Now you have the old 2.0.2 openoffice with nice fonts and everything you know from dapper, but the rest of the system is using the new libfreetype and edgy.
This worked for me, but no guarantee, so back-up everything first ;) 

okl

---

### Post by zilverling on 2006-10-28
Thanks for these instructions.

Do I have to type

export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8
oowriter

every time I want to start OpenOffice?

---

### Post by okl on 2006-10-28
The best would be to create a file called ooo in /usr/local/bin then chmod a+x ooo
the file should look like:

#!/bin/bash
export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8
oowriter



okl

---

