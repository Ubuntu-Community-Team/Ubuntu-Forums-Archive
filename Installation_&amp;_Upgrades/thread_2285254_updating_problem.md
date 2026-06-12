---
title: "updating problem"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by stefabarta on 2015-07-04
hi, i was doing my normal updating session from ubuntu, on terminal, with command: sudo apt-get update, and the updating was not done, and got this message at the end

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-it%5fIT

what do i have to do to go on? thanks

---

### Post by dino99 on 2015-07-04
this happens from time to time with always these i18n translation packages;can't says if it a server/reo issue or an index creation problem; but usually one of the next try succeed, so i've never paid to much attention to that issue (maybe test the 'main' server to get the updates).

you also can run: > sudo rm /var/cache/apt/archives/* to clean the room

---

### Post by v3.xx on 2015-07-04
More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Encountered+a+section+with+no+Package%3A+header&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Encountered+a+section+with+no+Package%3A+header&sa=Search&cof=FORID:9)

---

