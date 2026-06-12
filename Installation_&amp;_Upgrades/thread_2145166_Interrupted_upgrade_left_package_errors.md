---
title: "Interrupted upgrade left package errors"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by bonoetmalo on 2013-05-14
I'm not very clever with fixing issues. My upgrade to Raring was interrupted because I forgot it was running and I closed my laptop, and now I have a lot of dependency issues and package errors.

Here is the output of a few common fixes: 
sudo apt-get upgrade 
[LIST]
[*][http://pastebin.com/r7PX2jqA](http://pastebin.com/r7PX2jqA) 
[/LIST]
sudo apt-get -f install
[LIST]
[*][http://pastebin.com/VXV04ba2](http://pastebin.com/VXV04ba2) 
[/LIST]
sudo dpkg --configure -a
[LIST]
[*][http://pastebin.com/Ff03hxhk](http://pastebin.com/Ff03hxhk) 
[/LIST]
cat /etc/apt/sources.list
[LIST]
[*][http://pastebin.com/NB6MUMFp](http://pastebin.com/NB6MUMFp) 
[/LIST]

---

### Post by midnightramen on 2013-05-14
i had a partial upgrade to 13.04, when it hung during the kernel modules section. I was able to continue with the rest of the installation by re-running the Software Updater utility, and an option came up for a "partial upgrade" where it left off where it was before.

---

