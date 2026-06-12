---
title: "Should the r-base dependencies be updated for R to include inconsolata.sty?"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by dugthemathguy on 2012-06-29
I'm fairly new to Ubuntu and I hope this is posted in the right place. I am installing R under Ubuntu and I've run into a problem I think can be ironed out easily to help other people.
I decided to build R from source, but first I installed the dependencies using apt-get:
**$ sudo apt-get build-dep r-base**
when I configured gnu make for the R build everything went through except it complained that 'inconsolata.sty' was not found and this would prevent the R docs from being rendered correctly to .pdf
I found info here:
[http://r.789695.n4.nabble.com/inconsolata-font-for-building-vignettes-with-R-devel-td3838176.html]("http://r.789695.n4.nabble.com/inconsolata-font-for-building-vignettes-with-R-devel-td3838176.html")
and it looks like the problem is just installing one font that the R docs happen to use.
It can be installed ( along with a lot of other fonts ) with:
**$ sudo apt-get install texlive-fonts-extra**
My make and build went fine after doing that

So shouldn't 'inconsolata.sty' be included in the r-base dependencies so people aren't confused and so they can use the R docs?
I can image it might be a bad idea for everyone to install megs and megs of fonts on their machines like textlive-fonts-extra does,
but is their a way to include just the 'inconsolata.sty' font as a dependency?
I really have no idea who or how decides these things and don't pretend to know enough to really be part of that process but I thought I'd post this so that maybe if the people who do decide these things don't spend a lot of time using R, that maybe they could improve apt-get in a way they wouldn't have known about.
Doug

---

