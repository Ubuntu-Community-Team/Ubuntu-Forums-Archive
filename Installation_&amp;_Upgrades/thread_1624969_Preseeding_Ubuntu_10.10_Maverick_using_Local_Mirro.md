---
title: "Preseeding Ubuntu 10.10 Maverick using Local Mirror"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by skmah on 2010-11-18
Hello,

I've been installing Ubuntu with the preseed scripted install method since 7.04. The same preseed file seemed to work for all version since then except for 10.10 Maverick.

We point the installer to our internal server which has the Alternate CD ISO extracted. 

Since 10.10, the installer must have changed, as it's trying to hit gb.archive.ubuntu.com even though I'm using an internal mirror.

The d-i installer stops with the error:
Bad archive mirror. An error has been detected while trying to use the specified Ubuntu archive mirror.

my preseed file mirror section:
d-i mirror/country string manual
d-i mirror/http/hostname string {our internal http server}
d-i mirror/http/directory string /ubuntu/1010-64
d-i mirror/suite string maverick
d-i mirror/http/proxy string

I hope someone can shed some light on this.

thanks!

---

