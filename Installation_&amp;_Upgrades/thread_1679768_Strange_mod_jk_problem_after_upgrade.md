---
title: "Strange mod_jk problem after upgrade"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by John.Rayfield on 2011-02-01
I upgraded to v10 last night. It all went quite well, and there were no errors.

When I started my Apache, I found that web areas served directly by Apache were fine, but all of my WebApps served by Jboss (via mod_jk) were reporting 'Server cannot proces request'.

After much debugging of logs I found that mod_jk was having problems loading the **[FONT=Courier New]workers.properties[/FONT]** file.

I have **worker.list=jboss** but when mod_jk loaded the file it reported 'loaded **worker.list = jbsss**'

Yes, **[COLOR=Red]jbsss [/COLOR]**instead of **[COLOR=Red]jboss[/COLOR]**.

I changed **jboss **to **jbosxyz **and mod_jk said it was loading **jbosyzz **!!!!!

Something wierd going on here :mad:
Has anybody else heard of this ?

regards
John

---

