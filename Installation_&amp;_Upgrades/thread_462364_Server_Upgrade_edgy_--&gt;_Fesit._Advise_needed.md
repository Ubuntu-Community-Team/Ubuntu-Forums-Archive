---
title: "Server Upgrade edgy --&gt; Fesit. Advise needed"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by ranmanh on 2007-06-02
Hi,


I setup a little company server using kubuntu edgy. Postfix with courier, apache, mysql....etc...
Itook a while, as all of you can understand was the first system installation of these characteristics, not exprience on it and the system administrator needed something like kde. Kubuntu was the choice.
But now, ubuntu/kubuntu went into feist...  and I wonder whether if upgrading into feist or not.
The normal; fear, to crash the system, obviously the proper answer ghost  it".
Simple and straight question, anybody tried something like this before?? any extra advise I can take into consideration before trying anything at all?

I upgrade a regular dekstop system from kubuntu edgy to feist and went fabulous, no problem at all. But talking about a proper server, is another story.

Thanks for your words.

Gonzalo.

---

### Post by ranmanh on 2007-07-15
For your own records, it worked perfectly fine.
Some little tuning un relation with the mail server (clamd/amavis) and a BIG problem in apache2 with the geoip. It does not work in Fawn Feist.

The idea is... to download the source package, compile it manually and substitute the mod_geoip. (DO not uninstall the not working package, far better to keep the config files, and is only one file what is NOT working.)

I hope, if somebody got this problem. That is the best solution.

Thanks

Gonzalo.

---

