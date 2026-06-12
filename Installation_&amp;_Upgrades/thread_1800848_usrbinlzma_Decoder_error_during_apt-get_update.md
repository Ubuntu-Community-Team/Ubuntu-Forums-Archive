---
title: "usr/bin/lzma: Decoder error during apt-get update"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by schubi42 on 2011-07-09
after 

apt-get update

I am getting:


99% [127 Translation-en lzma 0 B] [Connecting to ie.archive.ubuntu.com (193.1.193.69)]/usr/bin/lzma: Decoder error
Fetched 8,433 kB in 3min 52s (36.2 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


I have rebuilt the sources.list, followed numerous MergeList work arounds - but none change a thing - at appears that in this case the /usr/bin/lzma: Decoder error
is essential to the issue.

Any ideas? Could an ISP transparent proxy be the issue? I have recently changed from ADSL to mobile broadband...

---

### Post by Rubi1200 on 2011-07-10
Hi and welcome to the forums :-)

Open a terminal and run these commands and post the output/errors please:

```
cat /etc/apt/sources.list

sudo apt-get update
```

---

