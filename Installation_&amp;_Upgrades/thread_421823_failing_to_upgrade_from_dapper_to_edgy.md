---
title: "failing to upgrade from dapper to edgy"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by garymcgarrigle on 2007-04-24
I'm trying to upgrade from Dapper to Edgy (and then on to Fiesty) but am having no luck. I'm given the option to upgrade to Edgy but I keep the these messages.


[IMG]http://farm1.static.flickr.com/225/471655628_ae28da00f9_b.jpg[/IMG]

[IMG]http://farm1.static.flickr.com/199/471655632_f17bae3be9_b.jpg[/IMG]

[IMG]http://farm1.static.flickr.com/172/471655636_5e6654e96c_b.jpg[/IMG]


any ideas on what I need to do? thanks.

---

### Post by Big Ed on 2007-04-24
Were you running compiz on Dapper?  

Anyway, I'd be taking a look at /etc/apt/sources.list and maybe commenting out the compiz lines.  One of you error messages also said something about a duplicate line.  Look for that also.

This site has a pretty extensive sources.list that you can compare yours to.  I wouldn't advise using the whole thing, just pick the line you need and update your sources.list.

[http://www.ubuntugeek.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.ubuntugeek.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

Ed

---

