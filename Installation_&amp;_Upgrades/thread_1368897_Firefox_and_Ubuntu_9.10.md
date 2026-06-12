---
title: "Firefox and Ubuntu 9.10"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by pek007 on 2009-12-31
hi,

few days ago i was upgrading ubuntu 9.04 to 9.10 and everything went ok, only firefox started to working with huge lag. sometimes it dont respond. i have opera also, but opera works fast. i mean normal. i tough that might be because it was not clean install.
yesterday i installed on another pc ubuntu 9.10 and it was clean install, but the problem was the same. firefox works really really slow, sometimes need 10s to load page, but sometimes works normal as it should. but i have also installed opera, to see if that is because of Internet connection, but opera works normal.
bout computers works on different Internet lines, so i don't think that might be a problem...

thank you for your help.

ziga

---

### Post by halovivek on 2009-12-31
can you please check and tell us what is the version of firefox you are using.

---

### Post by kevinatkins on 2009-12-31
I've noticed this, too. I think it's partly to do with IPv6 support and I've improved matters somewhat by disabling IPv6 support in Firefox.

In the address bar, type 

about:config

A warning screen will appear, click through that and you'll be presented with a bunch of options. In the filter box at the top, type 'ipv6' and a single configurable option should appear -

network.dns.disableipv6

Double-click on it and set it to 'true'

Then restart Firefox - you should see an improvement.

---

### Post by pek007 on 2009-12-31
firefox is version 3.5.6

now i will try with that. i hope it will work :)

ty for help

i tryed and it works wonderful. thank you very much m8.

see you

---

### Post by kevinatkins on 2009-12-31
You're welcome - glad it's sorted.

---

### Post by mkvnmtr on 2009-12-31
After reading this I decided to check my Firefox settings. I found in 9.04 that I had already changed the setting to true. Maybe when I was running 8.10. My Firefox is not very fast even with the changed settings. Then I booted my 9.10 and found that I needed to change the setting to true.Then on reopening Firefox it seems as fast as Chromium and Opera or even Midori. I should mention I am running the Development repositories in both 9.04 and 9.10. In 9,10 this has me using Firefox 3.5.8. It is very nice and now seems just as fast as the web-kit browsers.

---

