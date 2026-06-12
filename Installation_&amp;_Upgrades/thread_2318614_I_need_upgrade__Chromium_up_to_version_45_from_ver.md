---
title: "I need upgrade  Chromium up to version 45 from versión 37 in Ubuntu 12"
date: 2016-03-27
forum: Installation &amp; Upgrades
---

### Post by daniel-pbt on 2016-03-27
Hello, I need upgrade  Chromium up to version 45 or more. I actually use versión 37 in Ubuntu 12. I have to use a Google's app called Blockly, which is necessary to programme Picaxe microprocessors . This programme only runs  completely with versión 45 of Chromium. Can you help me please? I have read "thousands of webs" without luck
Thanks

Daniel

---

### Post by Bashing-om on 2016-03-27
daniel-pbt; Hello; Welcome to the forum.

I see but one way:
> 
You have searched for packages that names contain chromium-browser in suite(s) precise-updates, 
Package chromium-browser

precise-updates (web): Chromium browser [universe] 
37.0.2062.120-0ubuntu0.12.04.2: amd64 i386



Now in 14.04 :
> 
sysop@1404mini:~$ apt list chromium-browser
Listing... Done
chromium-browser/trusty-updates,trusty-security 49.0.2623.87-0ubuntu0.14.04.1.1112 amd64
sysop@1404mini:~$


and that is to install release 14.04. Else in 12.04 you will break your system in an attempt to install a later version of chromium-browser .

[INDENT][INDENT]newer can be better
[/INDENT][/INDENT]

---

### Post by daniel-pbt on 2016-03-28
Thank very much, I will install release 14.04.

Regards

Daniel

---

