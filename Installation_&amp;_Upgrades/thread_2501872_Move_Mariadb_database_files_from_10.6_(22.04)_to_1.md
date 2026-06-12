---
title: "Move Mariadb database files from 10.6 (22.04) to 10.11 (24.04)"
date: 2024-10-23
forum: Installation &amp; Upgrades
---

### Post by deck on 2024-10-23
I screwed up my 22.04 installation trying to fix a minor problem.  One issue is that I cannot get my backup drive (Western Digital Passport) to connect most of the time.  It may be hardware (old motherboard) or software.  So I have elected to do a bare metal upgrade to a new hard drive.  I have gotten 24.04 installed on the new hard drive and am trying to move files over.  The issue I am addressing here is moving the MariaDB files from MariaDB 10.6.18 to MariaDB 10.11.x.

I used mariadb-backup to create a backup of my all the databases for Wordpress and CQRLog (an amateur radio program).  The backup on 22.04 worked just fine.  Then I went to move the files to the mariadb version on 24.04.  I copied the backup files to the new drive.  Then I ran mariadb-backup with the "--prepare" directive.  I gave me a message that I needed to used mariadb-backup 10.7 or 10.6.  I tried installing version 10.6.18 and it wanted the mariadb-client 10.6 which would screw up my mariadb installation.  So where do I go from here?  I don't think I can upgrade the mariadb on 22.04 to 10.11 and I can't downgrade the mariadb on 24.04.  So where do I go from here?  Is there some other tool I can use?  Is there some other method I can use?

---

