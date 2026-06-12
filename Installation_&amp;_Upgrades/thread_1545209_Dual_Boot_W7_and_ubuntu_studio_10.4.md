---
title: "Dual Boot W7 and ubuntu studio 10.4"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by jackheart on 2010-08-03
Getting a new Laptop, Acer Aspire AS5251-1513 (damn good laptop for the price, and everything I want.)
Specs:[http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=86720&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=447&ctx1.att21k=1&CRC=3073651719](http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=86720&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=447&ctx1.att21k=1&CRC=3073651719)  

I have played a little around with linux, put puredyne on an old thinkpad, so I am familiar with some things, though I am still sort of a beginer.

My questions are:
Is it ok to use something like Wubi with windows7? 
I was curious about what sort of "risks" are involved (as stated on the Ubuntu pocket guide)?
And can wubi automatically set up my partitions and the proper formats?
Can I add a seperate partition for media/documents with Wubi or do I need to use gparted for that?
Should I use ubuntu studio 64 or 32 bit (if it is even available, wasnt sure on that one)

I am not planning on doing any crazy programing...yet. This computer is more for simple single user home use/artistic creations. I want to be able to write, work on photos and maybe do some editing plus go online. I really enjoy learning about linux but I am not about to go manipulate the kernel or anything like that. Sure I will have more questions...thanks!

---

### Post by oldfred on 2010-08-03
You can use wubi, but it is more for those users who are windows users and just want to try Ubuntu. If you are planning on staying with Ubuntu and using it a lot I would do a full install to partitions.  I prefer to create all partitions in advance with gparted and use manual install. But if you are shrinking a Win7 or Vista partition you should use windows tools and reboot windows several times before starting to install Ubuntu.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

