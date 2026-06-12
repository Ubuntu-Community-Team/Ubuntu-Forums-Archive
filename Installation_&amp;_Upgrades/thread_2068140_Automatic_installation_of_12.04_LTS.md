---
title: "Automatic installation of 12.04 LTS?"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by yanom on 2012-10-08
I found [this page]("https://help.ubuntu.com/10.04/installation-guide/i386/preseed-using.html#preseed-loading") about using preseeding to auto-install Ubuntu 10.04, but I can't quite figure out how to activate/use the automatic preseeding file they provided for an installation. Do those instructions even work for 12.04 LTS? 

Anyway, I need some way of running an unattended installation on 12.04LTS. Also, I'd like the installation to select the "log in automatically" option for the installer if at all possible.

---

### Post by Bucky Ball on 2012-10-08
It might help if we knew for what purpose you are setting up this system. For another end user than yourself?

---

### Post by yanom on 2012-10-08
yes. My school had a bunch of old unused computers they gave me and I'm putting Lubuntu on them to distribute around the community. I need a way to get a basic (I can tweak it later for each install site (password,hostname,user accounts etc)) install with those options running with those options automatically, because it's tedious setting each one up by hand.

---

### Post by yanom on 2012-10-08
...........bump

---

### Post by yanom on 2012-10-09
> **yanom said:**
> ...........bump

....................bump.

---

### Post by Bucky Ball on 2012-10-09
I think the plan might be to set one up then install via a LAN to the others. Is that what you're thinking??? Then you can install all at the same time. You might want to look there if you're not already. Log in automatically is easy 'one click' setting once installed. No menu list, no password is, I guess, what you're after.

There is also an OEM install option on the alternate install CD which has avenues to explore, though not sure if that will help.

You could dig through here for tips and clues:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A2oKmMtrv3RQWxUACZgK5gt.?p=multiple%20computers%20install%20ubuntu&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A2oKmMtrv3RQWxUACZgK5gt.?p=multiple%20computers%20install%20ubuntu&fr=altavista&fr2=sfp")


PS: From your link:

> If you are using initrd preseeding, you only have to make sure a file named preseed.cfg is included in the root directory of the initrd. The installer will automatically check if this file is present and load it.  Are you using this method and that's what you're having the issue with?

---

### Post by yanom on 2012-10-10
> **Bucky Ball said:**
> 

Are you using this method and that's what you're having the issue with?

I have a webserver on my home server machine, so I was going to put the preseed.txt file there and load it via network. Not sure how to do this exactly - I tried the ```
 auto url=http://192.168.1.67/preseed.txt
``` line in in the options line for "install Lubuntu", but that didn't load anything.

---

