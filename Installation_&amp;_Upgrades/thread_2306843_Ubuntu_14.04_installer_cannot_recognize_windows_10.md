---
title: "Ubuntu 14.04 installer cannot recognize windows 10 partitions"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by lolos11 on 2015-12-19
Hi. I have dell desktop with windows 10 with 3 partitions(i created one in order to install ubuntu) However When I run the setup for 14.04 using the live USB and select the option "something else" for manually creating partitions on my hard disk, ubuntu is unable to recognize my windows partitions!! How could ubuntu would "see" my partitions? I would like to have both systems in my pc. Thanks in advance




I think the below images may help you more:

---

### Post by blackwhite190 on 2016-01-21
I have the same issue on windows 10 while trying to install ubuntu 14.04. thanks for pulling out.

---

### Post by ubfan1 on 2016-01-21
Windows might be using "dynamic partitions", which Ubuntu cannot see.  Those "dynamic partitions" have to be converted into "basic" partitions.  Search this site for "dynamic" and see what you find.  I don't know much more about it than that.  The conversion process may be really bad, like having to copy everything off, repartition, and copy things back -- hope not.

---

