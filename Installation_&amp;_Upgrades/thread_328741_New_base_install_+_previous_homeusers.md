---
title: "New base install + previous /home/users"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by graabein on 2006-12-31
Hi, I am installing the base system anew with the **alternate cd**. My machine froze while upgrading to Edgy from Dapper so now I've wiped the smallest partition and set that up as **root**. 

I don't know what to expect when the install is done. Is **home** intact? It's on another partition but it was not marked with **home** on the partition menu. I did not touch it. Do I have to create new users and if so, will this delete the previous user directories?

---

### Post by radu_chindris on 2006-12-31
If it is on another partition it is still untouched. Choose it as the /home partition during the install but don't format it, create a different user than the existing /home/ user, proceed with the installation as usual. After the system is up, login as the new user, create a new user with the previous user name (previous_user, the existing home dir /home/previous_user won't be wiped out). Then all you have to do is fire up a terminal and type:
```

sudo chown -Rv previous_user:previous_user /home/previous_user

```
thus previous_user will gain ownership of the existing home contents.
Log out and log in as previous_user, you may choose to remove the user created during install.
Also, you may want to set the same password for the previous_user as for the user created during install so you don't have to type another password when sudo-ing
have phun

---

### Post by graabein on 2006-12-31
Thanks for the reply. I was thinking in the same lines with regards to creating a unique new user and later mapping the user directories with previous user names. I'll follow your instructions here. Thanks!

Looks like I forgot to map **home** when I reinstalled the base system so I'm doing it again now, leaving both **root** and **home** partitions unformatted but the install process still takes time...

I'll report back later. It's about time to get ready for new years celebration here in Norway. Get all suited and liqcuered up. ;)

Happy new year everybody!!

---

### Post by radu_chindris on 2006-12-31
Good luck and Happy new year! :)

---

### Post by graabein on 2007-03-29
Been a nice year thus far and I'm back on this old scrap heap (Pentium III-MMX 450 MHz). 

I have mapped up the previous users but I have a problem with the super-user, the first user created in Xubuntu Edgy Eft install. It has sudo rights while none of my previous users do... Where do I set this? Is it a particular group that has this setting?

---

### Post by dannyboy79 on 2007-03-29
this is similar to my question. can I use my home directory for 2 different ubuntu installs??? I want to run Dapper and Edgy on the same machine but then would like to share my home partition. IS this possible?

---

### Post by graabein on 2007-04-01
Well the answer to my problem was including the new user in the admin user group. This is done from *System > Users and Groups* dialog box. Now I can do **su** and enter user password again to carry out sudo commands.

---

### Post by louieb on 2007-04-01
> **dannyboy79 said:**
> this is similar to my question. can I use my home directory for 2 different ubuntu installs??? I want to run Dapper and Edgy on the same machine but then would like to share my home partition. IS this possible?
Sure its possible to share the home directory between 2 installs? It just need to be on its own partition. However Murphy's law and the law of unintended consequences can become big players when configuration files are shared by two versions of a program.

---

