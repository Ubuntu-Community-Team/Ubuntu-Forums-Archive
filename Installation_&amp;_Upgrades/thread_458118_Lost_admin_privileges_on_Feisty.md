---
title: "Lost admin privileges on Feisty"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by bikeman1 on 2007-05-29
I have apparently lost password privileges to my "sudo" account in a new install.   I was copying over passwd, gshadow, group, other files from /etc (I backed them up first) with those from another installation.  but apparently I trashed my ability to authenticate as admin.  Copied back the old files but to no avail.

I had no other users on the system.  I can't access console, users/groups, or synamptic, or any file manager with privileges.

Anyone have a clue how to rebuild/reset the configuration files?  Kinda tough without being able to get into a console. ........

---

### Post by aysiu on 2007-05-29
[This](http://www.psychocats.net/ubuntu/sudo) should help.

And while you're in recovery mode, ```
passwd *username*
``` should help you reset the password for your username.

---

### Post by bikeman1 on 2007-05-29
that's helpful!  But both console and recovery console come back with

/etx/sudoers is owned by gid=100, should be 0

I get the feeling I have corrupted my group database.  I am still in the "adm" and "admin" groups but not the "root" group.  Group 100 is the users group.  I think I reset the ownership on /etc/sudoers to users, when it wants to be root.....let me try and chown things back to normal

Sound right??

I do like learning about the recovery console, and appreciate the pscychocats page....:)

---

### Post by aysiu on 2007-05-29
Well, you're not supposed to be in the root group, but /etc/sudoers is supposed to be owned by root, so ```
chown -R root:root /etc
``` should help. And the command is case-sensitive. Make sure that's a capital *R*.

---

### Post by bikeman1 on 2007-05-29
yep, already on that.  Seems to get the usernames back up to speed.  whew!  Think I'll add a root password as a backup....

Also think I'll leave the userdatabases alone!  will mess with the samba and apache settings maybe but leave the authentication files as they be....

Thanks for your help!  I wouldn't have figured sudoers out for some time...this is my second day on Ubuntu and I really like it!:D

---

### Post by aysiu on 2007-05-29
So everything's working?

By the way, I wouldn't set a root password. If things get screwed up again and you can't figure out the root password, it's a bit more difficult to recover things, as recovery mode will prompt you for a root password.

---

### Post by bikeman1 on 2007-05-29
So I see....one can't login with at at the Gnome console anyway.  Well, how does one get rid of the password for root now that it is established??

The one really odd thing about this "don't login as root" setup is that the root permissions are still applied to system files.  So as a non-root administrator, its a constant battle against permissions.  As one of dozens of examples, how to edit samba.conf if your file editor won't open it because permissions aren't set correctly??  It seems to me that one could certainly get into trouble as a root user, but than one would also have the ability (also the know how) to get out of it.  The sudoers permissions were a good example.

---

### Post by aysiu on 2007-05-29
[quote=bikeman1]So as a non-root administrator, its a constant battle against permissions. As one of dozens of examples, how to edit samba.conf if your file editor won't open it because permissions aren't set correctly??[/quote] This is my take on it:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

And I don't know how to unset a root password...

---

### Post by bikeman1 on 2007-05-29
What you say (and write) is logical and well put.  I'm going to spend some time on your site.

Glad to meet you aysiu!

---

### Post by aysiu on 2007-05-29
No problem. Glad to have been of help.

---

### Post by bikeman1 on 2007-05-29
something still not right......

I am still having trouble authentivcaating files from my SUDO user.  And it doesn't seem to respect group membership.  All this started after a added a password to the root user.  

Here is an error I got trying to open a configuration file in /etc that had root ownership and user group.  

(gedit: 20406): GnomeUI WARNING ** while trying to connect to a session manager:
Authentication rejected, reason: None of the authentication proitocols specified are supported and host-based authentication failed

I suppose this is Ubuntu's way of telling me she doesn't trust me!  Seems like the trouble arises when I try to change the ownership of these files to anything but root.  But if  I set everything to root, I can't write or edit any files.....

A fine mess!!!  Is there any way to go into the rescue console and reset my SUDO user into good graces again??

Thanks.....boy this is frustrating (though I've had worse).

---

### Post by bikeman1 on 2007-05-29
Had some additional problems.  Somehow the added password for root was keeping admin group privileges from the SUDO user.  went back into rescue mode and added admin entries to sudoers, seemed to fix things.  Listen to what they say -- don't use root user!!! best to build file managers and consoles with sudo access and keep the permissions honest.  Will take some ghetting used to.

Thanks for the help!!!!!

bikeman1

---

### Post by bapoumba on 2007-05-30
> **bikeman1 said:**
>  Well, how does one get rid of the password for root now that it is established??

Hello,
```
sudo passwd -l root
```
[https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c]("https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c")
(Never tested it myself though).

---

