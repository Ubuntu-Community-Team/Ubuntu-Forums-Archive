---
title: "Don't know how to install a *.bin program in UU9.10"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by tommark on 2010-02-28
I downloaded a CRM (vtiger), which came as a *.bin program.  There are complete instructions on the vtiger site about installation, but I have to be logged in as "root".
I understand that "root" privileges have been excluded from UU910, how do I log is as a root user?  typing "su" doesn't do the job. No matter what I try, I get the "~", not the "#".
Thank you.

---

### Post by darkod on 2010-02-28
If the file is meant to be executed, I guess it already has the execute bit on. In that case I believe running from the folder where the file is

sudo bash filename.bin

should do the job.

---

### Post by darkod on 2010-02-28
Another option is:

./filename.bin

(yes, put ./ in front of the name)

But not sure if it works if sudo is needed. Give it a shot.

---

### Post by oldos2er on 2010-02-28
```
sudo -i
``` will give you a persistent root shell.

---

