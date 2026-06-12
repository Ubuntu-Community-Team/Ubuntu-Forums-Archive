---
title: "ntp.conf file missing?"
date: 2016-01-21
forum: Installation &amp; Upgrades
---

### Post by kman-devnull on 2016-01-21
Hi,
I want to install the ntp from source. So, I have taken the latest production version, and built it. But I don't find the "ntp.conf" file in /etc directory (or anywhere)

It configures and build goes through fine, but I don't see 'ntp.conf' file installed. What am I doing wrong? kindly advice.

=====
_Steps followed_
1. wget --no-check-certificate [http://www.eecis.udel.edu/~ntp/ntp_spool/ntp4/ntp-4.2/ntp-4.2.8p6.tar.gz](http://www.eecis.udel.edu/~ntp/ntp_spool/ntp4/ntp-4.2/ntp-4.2.8p6.tar.gz)
2. tar -xzvf ntp-4.2.8p6.tar.gz; cd ntp-4.2.8p6
2. ./configure
3. make
4. make install
=====

---

