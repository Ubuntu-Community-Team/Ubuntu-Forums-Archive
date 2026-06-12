---
title: "Noob here..."
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by kucelkj on 2012-12-28
Noob here.  I haven't filled my quota of dumb questions so here I go.

I'm brand new to Ubuntu.  I installed Server 12.04.1.  I've got networking working just fine.  I want to manage users and groups.  I want to give a user admin or sudo rights.  

I'm a Windows server guy that is considering using Ubuntu in certain situations as a Windows server replacement.  I need to do all the things I'm used to in Windows like: user/group administration, file permissions and so forth.

Thanks in advance for any help.  

-Ken

---

### Post by haqking on 2012-12-28
> **kucelkj said:**
> Noob here.  I haven't filled my quota of dumb questions so here I go.

I'm brand new to Ubuntu.  I installed Server 12.04.1.  I've got networking working just fine.  I want to manage users and groups.  I want to give a user admin or sudo rights.  

I'm a Windows server guy that is considering using Ubuntu in certain situations as a Windows server replacement.  I need to do all the things I'm used to in Windows like: user/group administration, file permissions and so forth.

Thanks in advance for any help.  

-Ken

The first user you create already has sudo permission.

To see if you have type

```
groups
```to add a user to sudo

```
sudo adduser <username> sudo
```

Remember the sudo password is your own login password, there is no need to enable the root account.  Also read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Bucky Ball on 2012-12-28
Welcome to the forums. ;)

For future reference, a title describing your actual issue/problem/question rather than 'noob here' or 'help please' or something generic, will get you more help. 

You can change the title of this one by hitting 'Go Advanced' and changing. This will change the title in the first post and when it comes up in the forum lists.

Good luck.

---

