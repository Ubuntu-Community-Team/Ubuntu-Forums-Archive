---
title: "How to get files update ( i don't want update from OS Ubuntu )"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by vietunion on 2007-04-13
Hi every1

First, sorry for bad English

Please tell me how to get all files update from Ubuntu.com ( or any site ), i have setup Ubuntu 6.10, it's work good but there are some file update available and i don't want update in ubuntu ( >200MB and update in my country is very slow )
i want file update ( ex: [http://www.ubuntu.com/](http://www.ubuntu.com/)............. ) and i can use IDM to download ( i will use windows xp to download and update for ubuntu )

Thanks very much :)

---

### Post by Jussi Kukkonen on 2007-04-13
At the moment there is no way to automatically download the needed files on another machine -- this is because the needed packages are different for every machine (different softare installed, different hardware drivers).

The best you can do is run "sudo apt-get update && sudo apt-get upgrade" and save the list of packages that would be upgraded. Take the list to another machine and download all of the packages by hand from packages.ubuntu.com. Move the packages to your Ubuntu machine and install them. This might be a lot of work -- I suggest you bite the bullet and just download the upgrades directly...

---

### Post by vietunion on 2007-04-13
Thanks very much, i will try late

Thank again :), i love ubuntu :D

---

