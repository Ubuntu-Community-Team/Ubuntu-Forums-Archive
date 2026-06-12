---
title: "Installation of New programs"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by ticknubbs on 2008-03-29
When I go to the Add/Remove programs under applications and try to install something I get the same error message over and over:"The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection." Number one, available is spelled incorrectly and Number two, it hit refresh because there is no 'Reload' button and try again and still the error message occurs....All I want to do is install some new programs....any insight?

---

### Post by Pumalite on 2008-03-29
Make sure that where it says 'Show', you have 'All Available Applications'
Also, you might have your /etc/apt/sources.list blocked.
Post:
cat /etc/apt/souces.list

---

### Post by Joeb454 on 2008-03-29
Do you have a working internet connection?

If so, then open Applications>Accessories>Terminal and run ```
sudo apt-get update
sudo apt-get upgrade
```

Note that you should run the above 1 line at a time :)

---

### Post by Pumalite on 2008-03-29
You can also go to System>Administration>Software Sources and put a check in every source that you deem appropriate.

---

### Post by ticknubbs on 2008-03-29
Thanks guys, I got it working now!

---

