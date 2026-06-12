---
title: "Problem with Preconfiguration File (Preseed)"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Markuss90 on 2007-11-14
Hello,

I have a problem with the mirror settings in my preconfiguration file.
The CD Image is located in the path http://<server-address>/kubuntu-606/
When I try to boot the Client the this error message is displayed

Bad Archive Mirror:
The Specified Ubuntu Mirror is either not available, or does not
have a valid release file on it. Please try a different mirror.

I've switched with alt+f4 and saw that he's trying to connect to
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release](http://archive.ubuntu.com/ubuntu/dists/dapper/Release)

why is he trying? I've configured that he should look in
http://<server-address>/kubuntu-606/

> 
d-i     mirror/country                   string  enter information manually
d-i     mirror/http/countries          select  enter information manually
d-i     mirror/http/directory           string  /kubuntu-606/
d-i     mirror/http/hostname         string  http://<server-address>
d-i     mirror/http/proxy                string
d-i     mirror/protocol                   select  http
d-i     mirror/suite                       select  dapper


thx

---

### Post by Markuss90 on 2007-11-15
*bump*

---

