---
title: "upgrade ubuntu server to where other server is upgraded to"
date: 2017-10-13
forum: Installation &amp; Upgrades
---

### Post by praneethu on 2017-10-13
Here is a scenario where there are 2 ubuntu machines. One is testing server and one is production server. 

To implement server upgrades, i need to upgrade the testing server on one day and if no issues seen even after 2 weeks, then i need to upgrade the production server till be date the testing server was upgraded to. 

I am not sure how i can implement it. Because, after 2 weeks, when i do [SIZE=1][FONT=century gothic]sudo-apt-get update[/FONT][/SIZE] and [FONT=century gothic][SIZE=1]sudo apt-get dist-upgrade[/SIZE][/FONT], i will be installing the packages which are newer and not tested on testing environment. 

I did search in this forums and in google, but i could not find something specific scenario like this. So, it would help if someone can guide me or share relevant articles regarding this.

---

