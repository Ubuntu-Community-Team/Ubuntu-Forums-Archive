---
title: "nslookup/nsupdate/host/dig libdns64: undefined symbol: GeoIP_country_name_by_ipnum_v6"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by bribera on 2010-04-29
A few days ago, I performed a clean installation using the 10.04 xubuntu RC install CD. I've installed all of the available package updates.

Most of the utilities that rely on libdns64 (i.e. those installed by dnsutils) are broken like so:

```
brendan@pequod:~$ nslookup
nslookup: symbol lookup error: /usr/lib/libdns.so.64: undefined symbol: GeoIP_country_name_by_ipnum_v6
```

I see similar errors when attempting to install bind9.

I found [an old thread that looks like a similar problem]("http://ubuntuforums.org/showthread.php?t=1345620"), but the files in question aren't quiet the same and I can't seem to find a working combination of changed symlinks. I also tried reinstalling the packages in question, to no avail.

If this affects you too, please mark that in the following bug report:
[http://bugs.launchpad.net/ubuntu/+source/bind9/+bug/571960](http://bugs.launchpad.net/ubuntu/+source/bind9/+bug/571960)

---

### Post by bribera on 2010-05-04
This was caused by the presence of an old version of GeoIP in /usr/local/lib.

My work uses a workstation bootstrapping script to quickly install all required tools and libraries. Instead of using the geoip-bin package, it downloads & builds an old version of geoiplookup. This added shared libraries that are incompatible with the newer dnsutils/bind9 packages. Deleting the old libs solved my problem.

---

