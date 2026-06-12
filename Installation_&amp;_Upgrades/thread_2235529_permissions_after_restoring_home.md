---
title: "permissions after restoring /home"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by johnfrith1 on 2014-07-21
I'm preparing to go from 12.04 to 14.04, and I have a question about home folder / file permissions.

I'm planning to reformat the disk,and then I will restore /home in a LiveUSB session (using Backup). Will I run into issues with permissions?

If the restored files will have the same permissions as they had originally, do I need to make sure the new user name is the same as the old one?

I'm having difficulty getting my head around this. What would I need to do? Thanks in advance for any help.

---

### Post by mikewhatever on 2014-07-21
> **johnfrith1 said:**
> I'm preparing to go from 12.04 to 14.04, and I have a question about home folder / file permissions.

I'm planning to reformat the disk,and then I will restore /home in a LiveUSB session (using Backup). Will I run into issues with permissions?
If you do it right, I don't think so. ...what's "Backup"?
> 
If the restored files will have the same permissions as they had originally, do I need to make sure the new user name is the same as the old one?

There are permisions (wrx), and there is ownership. If you change the username, the files will be owned by the old one. It's not hard to change ownership with the 'chown' command, but if you don't want to mess with that, keep the same username.

---

### Post by johnfrith1 on 2014-07-21
> **mikewhatever said:**
> If you do it right, I don't think so. ...what's "Backup"?
"Backup" is the backup utility included with 12.04. So "do it right" means if I don't mess up restoring?

> **mikewhatever said:**
> There are permisions (wrx), and there is ownership. If you change the username, the files will be owned by the old one. It's not hard to change ownership with the 'chown' command, but if you don't want to mess with that, keep the same username.
Ok. So I won't screw up permissions if I restore from a different username, or by using chown?

Thanks for that, mikewhatever.

---

### Post by mikewhatever on 2014-07-21
I think the backup tool in Ubuntu is called deja-dupe. I've not used it much, but pretty sure it should preserve permissions, ...gues that means it won't screw them, and chown only changes ownership. Anyway, we are here to help, so do not hesitate to ask, if anything goes wrong.

---

### Post by johnfrith1 on 2014-07-21
Yes, I should have said, it's called backup, but the help text refers to deja-dupe. 

Thanks mikewhatever. I'll start tomorrow, and it's a great comfort to know there are helpful people around. 

To twist Tenesse Williams - I've relied on the kindness of strangers, so I'll pass it on, (and try to be geneorous with it)!

---

