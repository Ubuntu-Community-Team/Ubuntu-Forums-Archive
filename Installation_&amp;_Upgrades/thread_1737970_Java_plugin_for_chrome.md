---
title: "Java plugin for chrome"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by j-peg on 2011-04-24
Hey i have been trying to get java to work in chrome so that i can play games and use my bank. But it seems too be a lot harder than i first thought, I have tried installing it by installing sun jave 6 on my computer and it works it just doesn't do anything for chrome, and i tried installing it by installing it through firefox but that was just as big a pain. can anybody help?

---

### Post by j-peg on 2011-04-24
ohh found a old thread on the forum they solved it like this ;)

Try to uninstall IcedTea Java browser plugin:
Code:
sudo apt-get remove icedtea6-plugin
And make sure you have installed Sun Java browser plugin:
Code:
sudo apt-get install sun-java6-plugin
Finally restart your browser and try again
writen by lykeion

;)

---

