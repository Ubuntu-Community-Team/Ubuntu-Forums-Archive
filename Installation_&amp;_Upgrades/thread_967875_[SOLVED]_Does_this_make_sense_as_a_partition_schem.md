---
title: "[SOLVED] Does this make sense as a partition schema for a LAMP server?"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by chrisofarabia on 2008-11-02
**Drive 	Partition	Type		Mounted on	Size**

Drive0 	
/dev/sda1 	Primary 	/ 		5 GB
/dev/sda2	Primary		/var		3 GB
/dev/sda3	Primary		/home		(remainder of disk)
/dev/sda4 	Primary 	(swap area) 	2 GB


Drive1
/dev/sdb1 	Primary 	/ 		5 GB
/dev/sdb2 	Primary 	/var	 	3 GB
/dev/sdb3	Primary		/home		(remainder of disk)
/dev/sdb4 	Primary 	(swap area) 	2 GB

Note: This is not a production server and is only intended as a home development box. It has two 320GB HDDs that are to be set up as RAID1

---

### Post by chrisofarabia on 2008-11-02
...bump

---

### Post by chrisofarabia on 2008-11-03
Anyone want to offer an opinion, or should I try a similar question in the server forum?

---

### Post by leg on 2008-11-03
Ok heres my opinion. If you are setting the server up so that users home directory is to be used as public facing then you are fine. If not and all material is to be stored in /var/www then I would have larger capacity there.

Also if this is not a production server I am not so sure I would bother setting up raid on it and use the second disk for something else. I would be tempted to have all the system stuff on disk 0 and split the second disk between /var and /home.

Hope this helps in some way.

---

### Post by chrisofarabia on 2008-11-03
Yep, that's the sort of information I'm looking for. I'm slowly getting my head around the way in which the file structures are set up in Ubuntu and han't twigged that /www was sitting under /var - so I'll adjust there. I'll keep the RAID1, just for that little extra protection - the chance are that I won't fill up the space any time soon and I'm comfortable I understand the set-up process.

---

### Post by chrisofarabia on 2008-11-06
Finally went with the following:

/ ] 5 Gb
/usr ] 5 Gb
/var ] 100 Gb
/home ] 208.1 Gb
swap ] 2 Gb

Got the RAID1 set up without any issues and install went on a treat at last.

---

