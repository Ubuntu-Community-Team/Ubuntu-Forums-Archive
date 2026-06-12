---
title: "Super Slow Boot after upgrading to Lucid"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by vfontanela on 2010-04-18
Hello, after upgrading to Lucid my boot became super slow.

I'm attaching my bootchart so you can tell me what's wrong, because I honestly don't understand the graphic very well.

Any help will be appreciated.

[http://img121.imageshack.us/img121/5408/vfontanelalaptoplucid20.png](http://img121.imageshack.us/img121/5408/vfontanelalaptoplucid20.png)

---

### Post by afrodeity on 2010-05-23
mine too.

[http://www.flickr.com/photos/14887361@N05/4624611874/](http://www.flickr.com/photos/14887361@N05/4624611874/)

and my [.xsession-errors log]("http://paste.ubuntu.com/438247/")

---

### Post by afrodeity on 2010-05-23
Strikes me that there should be an easier way to debug all of this, a machine readible log which we could feed to some central site which would spit out the solution?

---

### Post by dino99 on 2010-05-23
> **afrodeity said:**
> mine too.

[http://www.flickr.com/photos/14887361@N05/4624611874/](http://www.flickr.com/photos/14887361@N05/4624611874/)

and my [.xsession-errors log]("http://paste.ubuntu.com/438247/")

looking at your xsession, its fullfilled by errors about mozilla, cairo, foxyproxy, ...

so remove/purge .mozilla, cairo, ... (all packages complaining), then reboot and reinstall one by one (each time look at errors before installing the next package)

---

### Post by afrodeity on 2010-05-23
Ouch, but thank you.

---

### Post by afrodeity on 2010-05-23
Just a question about mozilla, do I remove firefox in the process? Bit of a headache. :(

---

### Post by dino99 on 2010-05-23
" .mozilla" is the hiden settings folder, and is recreated on next reboot (nothing to do about deinstalling firefox)

---

### Post by afrodeity on 2010-05-23
Aha, a general settings error caused as a result of the lucid upgrade which has no built-in system for triaging the problem presented by divergent system settings. Wish there was a more intelligent upgrade tool. 

Thanks, I think I'm in the right .ball park now. :)

---

### Post by dino99 on 2010-05-23
> **afrodeity said:**
> Aha, a general settings error caused as a result of the lucid upgrade which has no built-in system for triaging the problem presented by divergent system settings. Wish there was a more intelligent upgrade tool. 

Thanks, I think I'm in the right .ball park now. :)

have a nice play :guitar:

---

