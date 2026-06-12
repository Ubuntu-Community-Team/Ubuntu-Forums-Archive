---
title: "upgrade from edgy to gutsy.Production server"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by ivelasco on 2007-12-18
Hi there!

I have a important question(for me at least)

I have an production machine(mail server postfix,courier,squirrel,amavis etc),it works like a charm.but it is running under EDGY. so i must upgrade the system.
the question is must I do it step by step?This is, first upgrade to feisty an after gutsy?Or i have to do it straight to gutsy?
 IThis is the main mail server of a company and it is really important for us.Of course it is a 24x7 running system and I can't stop it.
 Other question would be if anybody knows any way to have a backup server fully sincronized with the main server and in case of a problem in the main, the backup server would be ready for working with all the main server data?I don't know if this is posible with rsync or something similar,the idea is that in the case that the main server fails the backup server be ready for to do the main server job,with the minimun settings changes.I



 
If anybody can tell me the steps for upgrade from EDGY to GUTSY and believe that this is posible to do in a critical machine,please,tell me how.
 The other posibility would be to migrate all the system to other machine running DEBIAN STABLE and after pass both to this system.But in this case the problem would be how to syncronize both machines for to keep all the users data and change the systems without losing mails.
 Both machines have two partitions one for system(/) and other one for home where are the users maildirs.What about the permisions?The uID must be the same on both systems?If are different will lose the permissions on the home directorios?(AKA the Mailboxes)


Thanks in advance

Best Regards

---

### Post by markusf21 on 2007-12-18
If possible I would suggest waiting until April for Hardy, since this will be the next LTS release.

---

