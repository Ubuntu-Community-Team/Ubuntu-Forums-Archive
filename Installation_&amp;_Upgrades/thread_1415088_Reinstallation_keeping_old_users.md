---
title: "Reinstallation keeping old users"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by ronso on 2010-02-24
My mother board broke and had to get a new CPU. I kept my old HD with Windows XP and Ubuntu 7.10. There were 4 users in Ubuntu and my account had administrator privileges. I reinstalled on top of the existing partitions for Ubuntu but only formated the root partition. I created my new account with the same name I previously had and to my surprise I was able to access all my files just like nothing had happened. So I tried to do the same with the other users and I created accounts with the same names as the original ones but I get the message "$Home/.dmrc not properly configured" when they try to log in. Is there any way I can successfully create these users?

---

### Post by darkod on 2010-02-24
Depending how you created the new users. To add a user for whom a home folder already exists, look at post #2 here:
[http://ubuntuforums.org/showthread.php?t=1308767](http://ubuntuforums.org/showthread.php?t=1308767)

That's how you should do it after reinstalling with keeping your /home partition.

---

### Post by argail1980 on 2010-02-24
Probably, you were just lucky, when creating your first user, so that it got the same UID as the old one.. usually the first user's UID is 1000.

open a terminal (Applications > Accessoires > Terminal) and type:

```
cd /home
ls -la
```

that should look something like

```

drwxr-xr-x   4 root root              4096 2009-05-31 22:00 .
drwxr-xr-x  21 root root              4096 2010-02-05 13:50 ..
drwxr-xr-x 104 myuser myuser          12288 2010-02-24 17:44 myuser
drwxr-xr-x 104 otheruser otheruser    12288 2010-02-24 17:44 otheruser
drwxr-xr-x 104 otheruser2 otheruser2  12288 2010-02-24 17:44 otheruser2

```

if there are numbers instead of names i.e.

```
drwxr-xr-x 104 1002 1002   12288 2010-02-24 17:44 otheruser
```

your old users had other UIDs. For instance, you could have created them not in the same order.
Suppose the name of the user is "otheruser", you can change the ownership of their directories with:

```
sudo chown -R otheruser:otheruser /home/otheruser
```

That should enable them to login again.

---

