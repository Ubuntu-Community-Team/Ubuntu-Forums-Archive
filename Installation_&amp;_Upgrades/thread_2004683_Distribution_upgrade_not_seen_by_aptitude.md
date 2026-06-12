---
title: "Distribution upgrade not seen by aptitude"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by patryk007 on 2012-06-16
From time to time I manually type in system's console: 
```
aptitude update && aptitude dist-upgrade -y
```I typed it a minute ago and pressed **Enter**. 
*Result:*  nothing new to install. 5 minutes later a prompt has appeared with a  question if I want to install **Ubuntu 11.10** (so far I had *11.04*). 

Why **aptitude** didn't noticed availability of a new **Ubuntu** distribution? 

*For your information:* Between the moment when I manually typed those commands and the moment when I saw prompt I have **not** typed: 
```
aptitude update
```


___________
[B]
PS. [/B]Originally I've posted this question on Debian User Forums (_***[click]("http://forums.debian.net/viewtopic.php?f=3&t=80773&p=439336")***_) because (AFAIK) **Ubuntu** and **Debian** have the same GUI update-manager (in Debian it's called *gpk-update-viewer*).
Unfortunately I was lynched by Debian's gurus (because of _*aptitude dist-upgrade **-y***_).

---

