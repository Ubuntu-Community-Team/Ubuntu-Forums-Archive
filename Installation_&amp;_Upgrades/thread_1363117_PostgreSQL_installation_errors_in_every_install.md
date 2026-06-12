---
title: "PostgreSQL installation errors in every install"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2009-12-24
Greetings.  I guess this goes into "installation & Upgrades" because it involves installation errors, though I am well beyond installing Ubuntu.

A few days ago, coincident with a crash that corrupted my gconf/gconfd structure, I started seeing errors on upgrading PostgreSQL 8.4; this although I was not trying to upgrade PostgreSQL.  I finally tried to uninstall PostgreSQL and reinstall it, one component at a time.

No good.  I still get the same error, only fewer because I am only trying to install one component: The engine itself.

Here is the output from Synaptic:

In the Installation Progress window:
> Selecting previously deselected package postgresql-8.4.
(Reading database ... 302782 files and directories currently installed.)
Unpacking postgresql-8.4 (from .../postgresql-8.4_8.4.2-0ubuntu9.10_i386.deb) ...
Processing triggers for ureadahead ...
Setting up postgresql-8.4 (8.4.2-0ubuntu9.10) ...
update-alternatives: using /usr/share/postgresql/8.4/man/man1/postmaster.1.gz to provide /usr/share/man/man1/postmaster.1.gz (postmaster.1.gz) in auto mode.
 * Starting PostgreSQL 8.4 database server
 * The PostgreSQL server failed to start. Please check the log output:
2009-12-24 00:36:00 EST LOG:  invalid IP mask "trust": Name or service not known
2009-12-24 00:36:00 EST CONTEXT:  line 110 of configuration file "_/etc/postgresql/8.4/main/pg_hba.conf_"
2009-12-24 00:36:00 EST FATAL:  could not load pg_hba.conf
   ...fail!
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error processing postgresql-8.4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up postgresql-8.4 (8.4.2-0ubuntu9.10) ...
 * Starting PostgreSQL 8.4 database server
 * The PostgreSQL server failed to start. Please check the log output:
2009-12-24 00:36:20 EST LOG:  invalid IP mask "trust": Name or service not known
2009-12-24 00:36:20 EST CONTEXT:  line 110 of configuration file "/etc/postgresql/8.4/main/pg_hba.conf"
2009-12-24 00:36:20 EST FATAL:  could not load pg_hba.conf
   ...fail!
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error processing postgresql-8.4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.4

In the "Error Occurred" box:
> E: postgresql-8.4: subprocess installed post-installation script returned error exit status 1

I underlined the reference to that conf file.  Just what is wrong with line 110?  Aha! I did it myself, at the suggestion of the authors of the book I have been using to learn PostgreSQL (Stones & Mathew): I had added this line:
> host   all    192.168.0.0      255.255.0.0            trust
There is no service named "trust"; hence the error upon startup of the server. :oops:

As it happens, by voicing the problem, forcing me to more closely examine my error messages, I have solved it. I have decided to post it after all, since it may be useful to someone (besides the curious crickets chirping out there in the silence :biggrin: ).  This is a confirmation of the maxim of Rabbi Chaim Soloveichik: > If you understand the question, you already have half the answer.
The reason for adding that line still applies but when it becomes necessary, I will post a question on a PostgreSQL forum/newsgroup.

---

### Post by DedMoroz on 2010-02-12
So what is the correct procedure to fix the PostgreSQL errors? Thanks!

---

