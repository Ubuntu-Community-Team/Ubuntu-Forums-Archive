---
title: "Unable to upgrade from 9.10 to Lucid Beta"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mitchellcipriano on 2010-03-21
I attempted to upgrade to the beta from my 9.10 install and I get the following:

[INDENT]An unresolvable problem occurred while calculating the upgrade:
Trying to install blacklisted version 'openoffice.org-filter-binfilter_1:3.2.0~rc4-1ubuntu1'

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
[/INDENT]
I do not think I have any unofficial software installed. I checked my sources and I have only Ubuntu sources selected. I did have some otter PPAs enabled prior to upgrading to 9.10.

How can I tell for sure?

---

### Post by kio_http on 2010-03-21
Try uninstalling OpenOffice from your system and then upgrading.

---

### Post by mitchellcipriano on 2010-03-21
> **kio_http said:**
> Try uninstalling OpenOffice from your system and then upgrading.

I was considering that. I will try it and see if it works.

Thanks!

---

### Post by mhenriday on 2010-03-21
**Mitchell**, uninstalling **OOo** and then upgrading will indeed do the trick ; check out my correspondence with **Phill** on [**[COLOR="Blue"]this thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=9002610"). But as I note there, the procedure wasn't precisely painless ; however, when you've finished and you re-install **OOo**, you will get the latest, **3.2** version....

Henri

---

