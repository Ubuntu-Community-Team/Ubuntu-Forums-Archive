---
title: "Where is firefox installed?"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by davethewave83 on 2013-12-22
In which directory is firefox installed? I tried /usr/bin but I cannot find the firefox.. I tried looking inside the /home/.mozilla folder but that's just got user profiles, surely it must be installed somewhere as I am using it ;P

---

### Post by vasa1 on 2013-12-22
What did you see when you typed **whereis firefox** in a terminal and pressed **enter**?
For more verbose output, try **locate firefox**.

And you can use **man whereis** and **man locate** to know more about these commands before running them. Also, just for completeness, you should run **sudo apt-get update** so that the database **locate** looks at is updated.

---

### Post by davethewave83 on 2013-12-22
That's a really useful and cool command thanks, but it's installed fairly complex it appears, rather than a single folder.
I've just download Firefox "Aurora" from Mozilla's website, it and it's all contained in one folder, I'm trying to find where regular firefox is so that I can replace it with this Aurora folder, is there a simple way to install Aurora? 

it says it's installed in 
/usr/bin/firefox
/etc/firefox
/usr/lib/firefox
/usr/bin/X11/firefox
/usr/share/firefox
/usr/share/man/man1/firefox.1.gz

I really just thought I could find a folder /usr/bin/firefox and replace the contents with that of this aurora package.

Edit**
I found three commands that make life a lot easier, I wish Mozilla would list these commands instead of giving a direct link to a package and no information on what to do with the package lol.. 

but here it is if anyone else needs 
sudo add-apt-repository ppa:ubuntu-mozilla-daily/firefox-aurora 
sudo apt-get update
sudo apt-get install firefox

---

