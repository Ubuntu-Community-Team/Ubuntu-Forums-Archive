---
title: "Ca not install thunderbird 3.0 or 3.1"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by donfisico on 2010-02-18
[FONT=Arial]Hi fellows, I have recently adquired a Dell Inspiron laptop with Intel Core 2 processor and Windows 7 Home Basic Edition (64 bits) installed. Since I need for working linux I have performed a reduction of the main partition of Windows leaving free a 20 GB of hard drive. With an Ubuntu 9.04 Desktop version (64 bits) I have installed then Ubuntu linux in the empty space mentioned now then having a dual boot laptop (I have done this before with other computers, I knew how to do it so to make it work). All went well and both OS works fine.  I have installed a lot of packs without any problem, when I installed thunderbird pack I notice that its version is 2.0. I didn`t think that was a problem until I wanted to install some addons [/FONT][FONT=Arial]and thunderbird complaints that those addons only work with versions superior to 3.0.  " Ok" I said to myself, and looked here:
[/FONT][http://www.addictivetips.com/ubuntu-linux-tips/how-to-install-thunderbird-3-in-ubuntu-jaunty-9-04/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-install-thunderbird-3-in-ubuntu-jaunty-9-04/)
and here
[https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=jaunty]("https://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=jaunty")
and here also
[http://https://edge.launchpad.net/+help/soyuz/ppa-sources-list.html]("http://https//edge.launchpad.net/+help/soyuz/ppa-sources-list.html")
(I think there are the right places to look, principally the two last ones). Then I folowed the instructions literally, and I had no problem in adding this ppa to sources and to retriving (apt-get update) the updates and list of packages from them. The problem is when I tried to install thunderbird by
*sudo apt-get upgrade*
or directly by
*sudoapt-get installf thunderbird-3.1*
then the answer is :
Can not find package thunderbird-3.1
or nothing to upgrade (in the first case).
 I am stucked here, do not know what else to do!

---

### Post by zvacet on 2010-02-19
```
sudo apt-get update
```

Find new Thunderbird version in synaptic and install it from there.You can also use [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") repo.

---

### Post by donfisico on 2010-03-04
Thanks, I have solved the problem.

---

