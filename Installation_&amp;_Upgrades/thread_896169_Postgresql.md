---
title: "Postgresql"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by joewest on 2008-08-20
I am fairly new to Linux, but I hate windows.  I read that Postgresql will do many of the things that MS Access would do, or at the very minimum allow me to build my databases without ever looking back. 
  I downloaded postgresql-8.3.3-2-linux-x64(2).bin.  I have no idea what to do with it next.  The book I have shows many instructions, none of which work for me.  It keeps referencing Red Hat, which I don't have.  It says to replace rpm with deb, but none of that works. 
  Is there somewhere I can search for proper instructions for Ubuntu to install this package, or perhaps I have the wrong package?  A book, or whatever will help get me up to speed.  I would appreciate any help I can get. :confused::confused:
  Joe West

---

### Post by Partyboi2 on 2008-08-21
I suggest following[[COLOR=Blue] this guide[/COLOR]]("http://hocuspokus.net/2008/05/13/install-postgresql-on-ubuntu-804/") the packages you need to install are in the ubuntu repos.

---

### Post by manishtech on 2008-08-21
Check the above link, it makes everything very clear
**postgresql** ==> Postgresql server
**postgresql-client** ==> Client 
**postgresql-contrib** ==>provides several additional features for the PostgreSQL database
**pgadmin3** ==> Web based frontend


I always recommend to use the package manager for installing anything. Just have  a look at it for any packages you want to install.

---

