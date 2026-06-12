---
title: "upgrade 12.4 -&gt; 12.4.1 and nothing works"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by MatsWolpers on 2015-03-15
i had an intranet server running 12.4.
i upgraded to 12.4.1 since my periodical apt-get dist-upgrade seemed to suggest it might be a good idea. when offered the choice, i said to keep the existing config files. nevertheless, after lots of calculation, the following are true:
- my apache service is no longer accessible
- my bugzilla is no longer accessible
- my local mail is no longer accessible
- my shared calendars are no longer accessible
- my shared contacts are no longer accessible
- my owncloud installation is no longer accessible
pretty much the only thing thats till works is file sharing.

it seems to me that somehow access rights handling has been changed despite my choice of keeping everything as it was before 
i cannot find any information that explains what happened.
i cannot find any pertinent information in the logs.
this is so incredibly frustrating, i just cannot face rebuilding this installation from scratch. it is only a toy server but it could have been my small business installation.

If anyone out there recognises the symptoms and can tell what switch i need to flip to make it all work again, i should be grateful.
thanks
mats

---

### Post by ian-weisser on 2015-03-15
> **MatsWolpers said:**
> seemed to suggest it might be a good idea.
When during your daily use did your system suggest that an upgrade might be a good idea? How did it propose this change to you?
If this was during an apt-get dist-upgrade, is the record of that session still in /var/log/apt/term.log?
Did your system, by chance, suggest a 'partial upgrade'?

> **MatsWolpers said:**
> it seems to me that somehow access rights handling has been changed
What is the exact error message you receive when you try to run these services?
Is the error message identical for all inaccessible services? If not, please let us know the exact error message for each.

---

