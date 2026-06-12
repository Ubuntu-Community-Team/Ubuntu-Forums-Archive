---
title: "issue with apache on multiple computers after os update"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by cedrickabongo on 2014-02-18
Hi,

As every second day, Yesterday morning I installed the updates on my computers. When i restarted them, apache does not find any of my application in /var/www/ not even a file that i create to the root of that directory. the error message is 404 not found. running sudo service apache2 status shows me that the server is running and browsing to localhost/ is showing me an empty file tree. I formatted one of the computer and re-installed the system. It worked until I run sudo get-apt update when adding new repositories (requirements to have my dependencies).  so now i am stuck... can't develop on my computers any more.

can someone help please.

they all run on ubuntu 12.04 LTS (64bit & 32 bit)

---

### Post by cedrickabongo on 2014-02-18
I found the solution. 

all my projects were in /var/www/ and the update just created /var/www/html/ and set it as the documentroot. 
well, can't explain how or why because the apache config file still have <Directory /var/www/> and i can't even see where /html/ where added in the config file.
this is the issue on all my computers. How can i report this issue with the last apache update ?

---

