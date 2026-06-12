---
title: "Edgy won't install"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by Squrdel on 2006-11-30
I have Dapper installed on an ext3 partition of a 320Gb IDE disk. I also have XP on a 120GB SATA drive. No problems with dual booting but I cant seem to get VMWare going with sound. I decided to download, burn and install Edgy without touching my Dapper installation until I was happy with Edgy.

I first tried to install it to an ext3 partition on the SATA drive. The installation starts and goes for a few minutes and then stops with a message saying 'installation fails'. After several tries with this I went to the primary partition on the IDE disk, formatted it ext3 and ran the installation again. Because the default action of gparted is to install Edgy over my existing Dapper I used 'manual partition'. I set all the partitions to mount correctly and my clean primary for '/'. I selected the 'boot' flag for this partition. The installer then says 'no root file system set'.

I have tried this over and over with various changes to partitions, etc., but to no avail.

Has anyone had this experience or know the fix? I would appreciate all comments.

---

### Post by Ruler on 2006-12-26
Squrdel did you ever solver this problem????
 
I have exactly the same problem, no matter what options I set - even though i am clearly specifing a partition for the Root file system, it still wont let me past that point. "NO ROOT FILE SYSTEM SET"
 
I did a succesful upgrade to Edgy but after a few unexplainable crashes the system is not so heathly and I really need to re-install but it just wont let me.
 
Why o why couldnt they keep an option for an 'old fashioned' install with out the pains of the live environment!   ](*,)

---

