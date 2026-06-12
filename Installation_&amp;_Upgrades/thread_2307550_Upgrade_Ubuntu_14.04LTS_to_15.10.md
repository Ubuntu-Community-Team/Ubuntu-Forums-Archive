---
title: "Upgrade Ubuntu 14.04LTS to 15.10"
date: 2015-12-26
forum: Installation &amp; Upgrades
---

### Post by kai15 on 2015-12-26
Hi, I have been using Ubuntu 14.04 LTS and I hear you can upgrade it to the latest Ubuntu version by changing the Update settings to any new Ubuntu version. However some people are saying this is not possible.

Should I wait for 16.04LTS instead? I am a bit wary of upgrading because I have a rather large /home partition and not many viable places to back it up to. (Upgrading from 14.04LTS to 16.04LTS would be a huge jump would everything still work OK seeing as 14.04LTS works fine)

---

### Post by mikewhatever on 2015-12-26
Upgrading the way you suggest is not impossible, but untested, and hence, not supported. Perhaps you succeed, and perhaps not. On the other hand, upgrading to 16.04 will be tested, and should be safer. What are the reasons for upgrade, especially if "14.04LTS works fine"?

---

### Post by cmcanulty on 2015-12-26
The usual rule is you can go directly from a LTS to another LTS but from a 6 month release you must do each successive 6 month release. So having 14.04 you could or should wait for 16.04. I have never had an issue doing this and that way you stay with the most stable releases. With a separate home partition it is even safer. That said I would try to back up home first and be sure when you upgrade to partition via something else and set /home to /home set to not format and set to use this partition. The default is confusing as if you don't hit change on the /home it will be set to not use.When you get to that point feel free to ask for a walk through of that part.

---

### Post by oldos2er on 2015-12-26
I would wait for 16.04, so that you can upgrade directly from 14.04 LTS to 16.04 LTS. Otherwise you'd need to go from 14.04 to 14.10 to 15.04 to 15.10; and because 14.10 is no longer supported, it complicates things. Plus that's a lot of upgrading to do, and much potential for things to go wrong.

---

### Post by grahammechanical on 2015-12-26
When it becomes time to release 16.04 the developers will work on upgrade scripts that will make the upgrade from 14.04 to 16.04 less risky. This work is done for every release of Ubuntu.

There are also things that we can do ourselves to lessen the risk. This is my advice. (a) revert to using an open source video driver. (b) remove any PPAs from the software sources list of repositories. (c) revert the user interface as close to default as possible. (d) remove any applications that were not installed through the Software Centre.

Remember, 14.04 will still have another 3 years of support before it becomes end of life. So, as 14.04 is still working fine (why would it not be?), why be in a hurry to upgrade? If you did manage to upgrade to 15.10 then you would have to upgrade to 16.04 within 6 months or thereabouts. Ubuntu 15.10 only has 9 months support & 2 months have already past by. Do you want to upgrade twice or only once?

Regards.

---

