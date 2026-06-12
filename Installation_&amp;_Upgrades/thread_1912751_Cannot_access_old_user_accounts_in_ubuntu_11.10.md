---
title: "Cannot access old user accounts in ubuntu 11.10"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by ifest on 2012-01-21
After upgrading from 11.04 to 11.10 I found that I cannot access(neither does it give me the option) old user accounts created in 11.04. They are visible as folders when accessing "home" folder (although cannot open them). Can anybody help?

---

### Post by Lars Noodén on 2012-01-21
The home folders are one thing, the accounts are another.  It's possible that the accounts are not there.  Are the usernames visible to you in [font=Courier New]/etc/passwd[/font]?

---

### Post by sudodus on 2012-01-21
If it is enough to access the folders and files, you should be able to run as root alias superuser, for example in a terminal
```
sudo ls -l /home/old-user
```
or using the file browser (in 'vanilla' Ubuntu: Nautilus)
```
gksudo nautilus
``` and browse to where you want.

It may be tricky to make it possible to log in to the old accounts again. [COLOR="Red"]I hope someone reading this can help you[/COLOR]. The old user accounts should work to upgrade to a new version, but obviously you were not lucky. Some people do fresh installs instead of upgrading to avoid such problems. At least, I think it is wise to

- make a complete backup
- test the new version live

before upgrading.

---

### Post by ifest on 2012-01-21
> **Lars Noodén said:**
> The home folders are one thing, the accounts are another.  It's possible that the accounts are not there.  Are the usernames visible to you in [font=Courier New]/etc/passwd[/font]?
Tried that but only got option to change passwd for the current account.  I guess the accounts have been lost...

---

### Post by ifest on 2012-01-21
> **sudodus said:**
> If it is enough to access the folders and files, you should be able to run as root alias superuser, for example in a terminal
```
sudo ls -l /home/old-user
```
or using the file browser (in 'vanilla' Ubuntu: Nautilus)
```
gksudo nautilus
``` and browse to where you want.

It may be tricky to make it possible to log in to the old accounts again. [COLOR="Red"]I hope someone reading this can help you[/COLOR]. The old user accounts should work to upgrade to a new version, but obviously you were not lucky. Some people do fresh installs instead of upgrading to avoid such problems. At least, I think it is wise to

- make a complete backup
- test the new version live

before upgrading.
Thanks, but it didn't help.  I just need to access the files on the old accounts.  I would have backed up before upgrading, but on a different computer I did the same upgrade(after backing up) and it retained the accounts.  Thus, being lazy, I thought it would do the same on this computer and didn't backup.  Just my luck I guess....

---

### Post by sudodus on 2012-01-21
What if you use the following command (now with the options -la), and remember to substitute ***'old-user'*** with the real name of each old user account, actually each directory in /home
```
sudo ls -l /home
```
```
sudo ls -l[COLOR="Red"]a[/COLOR] /home/[COLOR="red"]old-user[/COLOR]
```

---

### Post by ifest on 2012-01-21
Whoohoo!!! Solution is as simple as can be!! Just needed to create new user accounts with same usernames and passwords as old ones and bingo, problem solved!  Thanks for all your help people!:D

---

### Post by Lars Noodén on 2012-01-21
Excellent. I thought it would be something like that.  Be sure that the names match the numbers.  It is the numbers that are relevant.  You can do that by using **-n** on /home:

```

ls -n /home

```

---

