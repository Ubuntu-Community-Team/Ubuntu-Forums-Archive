---
title: "How to Migrate Postgresql 9.0 to 9.1"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by saphil on 2011-10-07
I am running Ubuntu 10.04, on production servers.
I am running backports because my software is now requiring Postgresql 9.0
I got my Postgresql 8.4 databases updated to Postgresql 9.0
That worked pretty well and with a ton of research, and some help from friends, everything was fine.

Recently the repos started putting out Postgresql 9.1
I saw that the installer looked like it was updating my databases automagically, however I don't want to migrate production boxes unless I am sure.
Postgresql 9.1 appears to be listening at port 5433 (rather than 5432 where all my software expects it to be) and 9.0 is still at the same old stand at port 5432.

The documentation I can find is written presupposing a lot of prior knowledge, and is not helping my peace of mind at all.  Has anybody written a basic step-by-step how-to for this - for Ubuntu 10.04?

-Wolf

---

