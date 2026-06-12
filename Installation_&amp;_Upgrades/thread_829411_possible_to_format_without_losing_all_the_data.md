---
title: "possible to format without losing all the data?"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by cravonic on 2008-06-14
i have 2 partitions

/ and /home

i want to format the ubuntu partition without loosing firefoxe's 

plugins, history and favories, i also don't want to loose thunderbird 

and other programs, 
is it possible to format whithout loosing all the data, considering 

that they all are in the home partition?

how can i keep all the software i installed and all of its definitions?

thanks

---

### Post by Pumalite on 2008-06-14
If you are reinstalling; go Manual, choose the old partitions, but don't format /home. You can ignore /swap

---

### Post by Fingel on 2008-06-14
You can't format without losing data. you can however format the / partition but keep your /home partition. That way you will keep your personalized data, and when you reinstall your apps the settings *might* be saved.

---

### Post by cravonic on 2008-06-14
how create the user?

put the same name?

---

### Post by Pumalite on 2008-06-14
Same name and password.

---

### Post by Habbit on 2008-06-14
Furthermore, if you have several users, you should create them in the same order to make sure every user gets the same UID it had - if you don't, hell is sure to break loose. Another option is to create each user specifying its UID (iIrc, with useradd -u uidnum).

---

### Post by cravonic on 2008-06-15
it has the certainty of what they are to say, already had made this?

I create user in the assistant or later for it consoles? how he is safer?

---

### Post by Habbit on 2008-06-15
> **cravonic said:**
> I create user in the assistant or later for it consoles? how he is safer?

It is not a question of security: both are just as safe, but useradd allows you to choose the UID assigned to new new user while the wizard generates a new one automatically.
You said you wanted to keep the /home partition without losing data, so you need to make sure that the users you re-create match the pre-existing ones, because only the UID is saved in the filesystem structures. Let me put an example: in my computer, I have two interactive users, family and habbit, which have UIDs of 1001 and 1000 respectively. If I reinstalled Ubuntu while keeping my /home partition and then created the users in the wrong way, "family" would get UID #1000 and "habbit" would get #1001, thus exchanging owership of their home folders.

Most probably, the best you can do is invoke "ls -n" in your /home partition, to get a result like this:```
drwxr-xr-x 28 1001 1001 1080 2008-06-14 13:01 family
drwxr-x--- 79 1000 1000 3544 2008-06-15 13:33 habbit
```If you don't use the "-n" option, unknown users (like 1001) will be shown as their UIDs, but the user #1000 is known in the Ubuntu LiveCD environment - it's user "ubuntu". Thus, my home folder would have shown as being owned by the "ubuntu" user. With "-n", ls makes no attempt to resolve the UIDs into names. Then, you know what UID to assign to each user once you have the system installed: ```
# adduser --group --uid 1001 family
# adduser --group --uid 1000 habbit
```
The last command may fail because there will already be an user #1000, the one you created in the installation process, so you should directly create the "right" user (that is, the one with oldUID=1000) in the installation.

---

