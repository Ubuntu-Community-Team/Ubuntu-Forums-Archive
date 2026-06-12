---
title: "Fresh 12.04 installation and noticed worrysome outbound connections"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Dopameen on 2012-05-30
I just installed 12.04 Pangolin and was a bit worried. The following domain connections are made:
ntp.ubuntu.com
geoip.ubuntu.com
geoip.ubuntu.com
videosearch.ubuntu.com
changelogs.ubuntu.com
extras.ubuntu.com
security.ubuntu.com
security.ubuntu.com
archive.ubuntu.com

In particular, it are geoip.ubuntu.com and videosearch.ubuntu.com which worry me. The first I found out is used by Geoclue. This is in fact geographical tracking software. I find it appalling that there is no other way to know of the existence than to use a packet sniffer. Disabling it should be rather easy... [http://askubuntu.com/questions/142581/is-ubuntu-geoip-geoclue-is-used-for-tracking](http://askubuntu.com/questions/142581/is-ubuntu-geoip-geoclue-is-used-for-tracking)

The other domain is videosearch.ubuntu.com. There is very little I could find about this. Anybody who knows which applications calls videosearch.ubuntu.com and why?

---

