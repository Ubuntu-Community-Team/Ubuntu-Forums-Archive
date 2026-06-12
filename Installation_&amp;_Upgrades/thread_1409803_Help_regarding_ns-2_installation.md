---
title: "Help regarding ns-2 installation"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by ashwintk on 2010-02-18
I installed ns2-2.34  version on Ubuntu-8.04
I followed the steps given below

*tar xvfz ./ns-allinone-2.34.tar.gz*
*cd ns-allinone-2.34*
*sudo apt-get install build-essential autoconf automake libxmu-dev*
*./install*
*gedit ~/.bashrc*

Then I Updated the path 

source ~/.bashrc

then if i run ns  its displayin the following message instead of % prompt

Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]

---

