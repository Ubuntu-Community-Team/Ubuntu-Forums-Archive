---
title: "OpenOffice 3.2.1"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by teejay17 on 2010-06-08
Are there plans to put the newest OpenOffice 3.2.1 into the repositories; plans to update it automatically?

---

### Post by snowpine on 2010-06-08
Currently OO3.2.1 is included in the testing repositories for 10.10 Maverick. It is possible Canonical will "backport" it to older Ubuntu releases, generally this is only done for security patches, bug fixes, etc.

---

### Post by teejay17 on 2010-06-08
> **snowpine said:**
> Currently OO3.2.1 is included in the testing repositories for 10.10 Maverick. It is possible Canonical will "backport" it to older Ubuntu releases, generally this is only done for security patches, bug fixes, etc.

Thanks. I was just wondering if I should wait for an "official" Ubuntu update, or just go ahead and uninstall the old and install the new. 
I am using 10.04.

---

### Post by darkod on 2010-06-08
If you don't plan to upgrade to 10.10, then just remove 3.1 and install 3.2.

No need to upgrade every 6 months with the new release, 10.04 is LTS.

---

### Post by teejay17 on 2010-06-08
> **darkod said:**
> If you on't plan to upgrade to 10.10, then just remove 3.1 and install 3.2.

No need to upgrade every 6 months with the new release, 10.04 is LTS.

Oh goodness no, I wouldn't change from 10.04 just because of Open Office; I don't event think I will bother with 10.10. It sounds too experimental. As long as I can just upgrade programs like Firefox and OpenOffice, I'll be sticking with 10.04.
On an other note, I've found this article [here ]("http://www.muktware.com/news/08/2010/164")detailing how to upgrade to the newest OpenOffice.
Would everyone concur that this is a good method?

---

### Post by darkod on 2010-06-08
> **teejay17 said:**
> Oh goodness no, I wouldn't change from 10.04 just because of Open Office; I don't event think I will bother with 10.10. It sounds too experimental. As long as I can just upgrade programs like Firefox and OpenOffice, I'll be sticking with 10.04.
On an other note, I've found this article [here ]("http://www.muktware.com/news/08/2010/164")detailing how to upgrade to the newest OpenOffice.
Would everyone concur that this is a good method?

Looks OK. If the downloaded and unpacked files are .deb I think right-click Install would work too, no need for terminal. But first do the step to remove the old version.

---

### Post by Onesimus on 2010-06-08
> **snowpine said:**
> Currently OO3.2.1 is included in the testing repositories for 10.10 Maverick. It is possible Canonical will "backport" it to older Ubuntu releases, generally this is only done for security patches, bug fixes, etc.

But I thought that OOo 3.2.1 was a security patch and bug fix - hence it should appear in the repositories for 10.04

---

### Post by claracc on 2010-06-09
Yes, you are right Onesimus, openoffice 3.2.1 is a bugfix release as they say in release notes.

So, could we can expect this release will be included in some of the ppa's (openoffice.org Scribblers)?

Thanks in advance

---

### Post by Onesimus on 2010-06-09
I have already downloaded the new OOo 3.2.1 from the repositories.  If you start up Update Manager it should appear.

---

### Post by teejay17 on 2010-06-09
> **Onesimus said:**
> I have already downloaded the new OOo 3.2.1 from the repositories.  If you start up Update Manager it should appear.
That's good news. I will try that tonight when I get home.

---

### Post by Hagar Delest on 2010-06-09
OOo 3.2.1 is a bugfix release (like all the X.Y.1 OOo versions). But it's not a security issue so it won't appear in the repositories.

If you want the command line memorized in your shell history, you don't need to copy the whole lines with the file names. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Subito Piano on 2010-06-14
When should one expect version 3.2.1 to be available in the repos?  I am running Ubuntu Studio 10 and the repos just got up to version 3.2.0 and need my navigation buttons working correctly when exporting Impress as html slides (described [here]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=29129&start=0")).  I am hoping the release addresses this problem...  :-(

---

### Post by Subito Piano on 2010-06-14
Never mind!  I found [this thread]("http://ubuntuforums.org/showthread.php?t=1350095").  Works beautifully now.

---

### Post by gechert on 2010-06-17
I installed OO 3.2.1 after downloading it from Oracle/Sun (I did not see it in the repositories last time I looked).  I got an error message saying I did not have Java installed.  Apparently 10.04 does not support Java? (I did install Java some time ago.)  So, I installed the "JDK" from the repositiories.  I had been having problems with 3.2 not handling a large excel spreadsheet which OO 3.1 was OK with.  Now, 3.2.1 is fine with it and also seems to work with ".doc" files better than even 3.1.  Not sure if the improvement is due to the upgrade or to the JDK - but if it's due the upgrade, I'd say  3.2.1 is much more than a bug fix.

---

### Post by Hagar Delest on 2010-06-17
The JDK has nothing to do with it I think. You have to make sure that in Tools>Options>OOo>Java, there is a version _checked_. NB: wait a while until OOo has scanned the system for the java versions.

---

