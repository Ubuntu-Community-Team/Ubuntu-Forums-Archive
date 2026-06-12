---
title: "Migrate to Software RAID1 with Encrypted LVM"
date: 2020-01-24
forum: Installation &amp; Upgrades
---

### Post by r00nster on 2020-01-24
I have an exiting Ubuntu server (v18.x). 
The server has a single hard drive and with an encrypted LVM. This was all done using the standard installation procedure (nothing special)
The server also has LAMP installed with an application running on top of it.

The system is running without any problems but I have a spare identical hard drive and want to install this and use Software RAID1 to mirror the data incase of drive failure.

What is the easiest way to convert the existing installation (single drive with encrypted LVM) to an installation with dual drives, Software RAID plus an LVM volume, LAMP & application ?

Can I convert this in-place somehow or do I have to start again from scratch as in... 
1. Backup my LAMP application (configuration, Database, web files etc.)
2. Re-install Ubuntu from scratch with Software RAID & Encrypted LVM
3. Install LAMP
4. Restore my configuration, Database & web files.

I've seen articles on how to install software RAID & encrypted LVM from scratch but can't find anything on how to convert and existing installation.

Thanks in advance...

---

### Post by CelticWarrior on 2020-01-24
I've no experience with servers but...

Yes, your plan makes sense if using Software RAID.
Otherwise, with a RAID controller you'd used that to build the RAID from your existing installation.

---

