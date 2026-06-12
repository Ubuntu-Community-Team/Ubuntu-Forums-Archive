---
title: "preseed file did not work in pxe isntallation"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by richard_wu0313 on 2011-05-11
hi forks,
i created a preseed file to auto install ubuntu10.10 x64 image, but these config in preseed file seemed not working. i only listed some items such as setting language, keyboard, time and son

[COLOR="Blue"]d-i debian-installer/locale string en_US

d-i netcfg/get_hostname string xxxxxx
d-i netcfg/get_domain string xxxx

d-i clock-setup/utc boolean true

d-i time/zone string US/Central[/COLOR]

any idea? thanks!

---

