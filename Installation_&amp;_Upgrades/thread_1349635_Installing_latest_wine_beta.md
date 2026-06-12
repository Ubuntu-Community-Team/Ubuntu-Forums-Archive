---
title: "Installing latest wine beta"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Charkel on 2009-12-08
How do I install the latest wine beta? I followed the instructions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
First i added ppa:ubuntu-wine/ppa and then i ran sudo apt-get install wine
but it still installs the 1.0.1 :\

I'm using Karmic 9.10

EDIT:
SOLVED!!!
All I had to do was run "sudo apt-get unpdate" and the include a version number like so "sudo apt-get install wine1.2"

---

### Post by Sharft 6 on 2009-12-08
the latest wine beta is 1.1.34. I type in 

sudo apt-get install wine1.1.34

and it says

Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package wine1.1.34

---

### Post by Charkel on 2009-12-18
> **Sharft 6 said:**
> the latest wine beta is 1.1.34. I type in 

sudo apt-get install wine1.1.34

and it says

Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package wine1.1.34

Did you follow the steps I did? I wrote wine1.2

---

