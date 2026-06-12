---
title: "Essential Upgrade Required Sooner then Later (need ideas)"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by bxdobs on 2014-08-10
Hoping someone may know of a way to force an upgrade of Gutsy without doing a clean install (the assumption is that an upgrade would still retain the Gutsy configuration(s) required to run a custom web app)

Objectives:
1) move Ubuntu Server to new Hardware
2) provide an ODBC link to SQL data for MS Access  

Background:
Non-Profit Association using a custom built POS (PHP Web) Application served from an old UBUNTU Server for several years.  

Gutsy Gibbon 7.10  (appears to no longer be supported for update (apt-get update) or upgrade (do-release-upgrade))
java-1.5.0 Sun      (requires ubuntu upgrade before update) 
apache             
tomcat 5.5.25       (requires ubuntu upgrade before update) 
mysql                  (requires ubuntu upgrade before update)
odbc                   (unknown)

While this web app serves its purpose as a POS, without an SQL ODBC link, it is an accounting nightmare (daily balancing involves double entry from printed reports into excel and simply accounting) The Hardware for this POS Server is also living on borrowed time even with spare parts. Several quotes for POS Software capable of replacing this application all have 5 digit price tags. Initial costs aside, the annual support fees by themselves, are beyond this group's means. 

I have gone after this from several directions:

- update and or upgrade ubuntu and services (failed as detailed above) the intent is once upgraded, the image should be movable to new hardware plus provide a proper ODBC link.

- move the php application to a fresh ubuntu install (not clear what is required configuration wise for this application to work properly ... needs more research) 

- reverse engineer the application (there are a number of jar classes that have no source and the jar to class converters won't resolve)

- move to VM Player ... there are issues within VM ... the GUI interface will not start as it is not recognizing the existing display driver (one forum suggested removing drivers but we get back to; as Gutsy is no longer supported, finding another suitable driver may not be possible) ... a VM can be run on new hardware so this could still be a solution coupled with automated data syncing

- Nightly automated syncing of SQL data to a link-able database (dump and reload) ... concerned with data integrity, Plus by itself, this doesn't resolve the hardware issues.

---

### Post by tgalati4 on 2014-08-11
I assume POS means Point-of-Sale.  You have described a difficult situation.  An in-place upgrade of Gutsy (Ubuntu 7.10) will surely cause breakage--your old hardware will probably have problems with 12.04 or 14.04 because of the much-newer kernel versions.

I would try to upgrade 8.04 first and change your /etc/apt/sources.list with any reference "achives" to "old-releases" then perform an update.  Run that for a while.  Then attempt to make a jump from 8.04 to 10.04.  Run that for a while.  Then jump to 12.04 and stick with that through April 2017.

For ODBC, you need to install a connector to mysql.  I'm not sure how easy this is.  You need to confirm the oldest version of ODBC that your MS Access database is compatible with.  [http://www.mysql.com/products/connector/](http://www.mysql.com/products/connector/)

There are a lot of ODBC hooks in the repostitories, you will need to investigate exactly what you need:

```
apt-cache search ODBC
```

You could set up a two-step process:  export the data you need to LibreOffice database (which supports ODBC) then run a script to export the LibreOffice database to MS Access.

Because your system is old (at least 7 years) I would be inclined to get new hardware and refactor the entire POS system using newer frameworks.  Keep the old system in place until you have the new service working correctly.

---

### Post by oldfred on 2014-08-11
I used to use MS Access to connect to a lot of different databases, MS SQL, Btreive, IBM AS/400, but never to any open source db.
I do have this in my notes.

[http://dev.mysql.com/downloads/connector/odbc/](http://dev.mysql.com/downloads/connector/odbc/)

But I always had issues getting the initial ODBC configuration correct in Windows and MS Access, but that was back with XP and Access 2000, so I am sure it is different now.

---

