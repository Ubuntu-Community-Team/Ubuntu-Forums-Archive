---
title: "Preseed Install fails to create user account"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by kuhn on 2008-11-14
Hello,

I am working on creating a custom ubuntu dvd based on 8.04 using a preseed file. Most stuff is working, however I want to have the install automatically create a normal (non-root) user account which it fails to do. I'd like to be able to do so without prompting for a username or password at install time.

From reading the instructions it seems this should be straightforward by using the following in the preseed file: 

d-i passwd/make-user boolean true
d-i passwd/user-fullname string Video User
d-i passwd/username string viduser
d-i passwd/user-password password somepasswd
d-i passwd/user-password-again password somepasswd

However, when I run the installation the user has not been created. I tried looking for an error message of some sort in /var/log/installer/syslog, but I don't see anything that looks relevant.

When I look in the file /var/log/installer/cdebconf/questions.dat, I see that the value of passwd/username was set to "viduser", so the installer seems to get that information correctly. However, a search for the string "user-password" in this file (questions.dat) returns no results - so it's as though maybe the password info is not getting read or parsed correctly. I have double and triple checked that I spelled everything right, and used only a single space between fields in the preseed file.

Anybody have any ideas about this, or advice how to debug what is happening? Any info will be appreciated.

Regards,
Scott

---

### Post by kuhn on 2008-11-17
Hi,

A bit more information on this. I added DEBCONF_DEBUG=5 to the kernel parameter list and tried again. After doing this I see the text shown below, in /var/log/installer/syslog on the installed system:

Still there are no obvious error messages shown. The only part that looks strange is that certain values don't exist (see **bold **below) and have to be registered with debconf. Does anybody know if that is normal? Maybe this is an indication that I'm using the wrong varible names to try to create the user, however I've seen these variable names used in several example preseed files...

Also note, in the preseed file that was used to generate the output below, I changed to use a hashed password, instead of using cleartext. (I thought that might fix the problem). So instead of 
d-i passwd/user-password password somepasswd
d-i passwd/user-password-again password somepasswd
Now I've just got
d-i passwd/user-password-crypted password <hash>


```
Nov 17 19:37:01 debconf: --> SET passwd/user-fullname Video user
Nov 17 19:37:01 debconf: <-- 0 value set
Nov 17 19:37:01 debconf: SUBST passwd/user-fullname ID passwd/user-fullname
Nov 17 19:37:01 debconf: <-- 0
Nov 17 19:37:01 debconf: FSET passwd/user-fullname seen true
Nov 17 19:37:01 debconf: <-- 0 true
Nov 17 19:37:01 debconf: SET passwd/username viduser
Nov 17 19:37:01 debconf: <--10 passwd/username **doesn't exist**
Nov 17 19:37:01 debconf: REGISTER debian-installer/dummy passwd/username
Nov 17 19:37:01 debconf: <-- 0
Nov 17 19:37:01 debconf: --> SET passwd/username pvuser
Nov 17 19:37:01 debconf: <-- 0 value set
Nov 17 19:37:01 debconf: SUBST passwd/username ID passwd/username
Nov 17 19:37:01 debconf:Adding [ID] -> [passwd/username]
Nov 17 19:37:01 debconf: <-- 0
Nov 17 19:37:01 debconf: FSET passwd/username seen true
Nov 17 19:37:01 debconf: <-- 0 true
Nov 17 19:37:01 debconf: SET passwd/user-password-crypted <hash>
Nov 17 19:37:01 debconf:  <-- 10 passwd/user-password-crypted **doesn't exist**
Nov 17 19:37:01 debconf: REGISTER debian-installer/dummy passwd/user-password-crypted
Nov 17 19:37:01 debconf: <-- 0
Nov 17 19:37:01 debconf: SET passwd/user-password-crypted <hash>
Nov 17 19:37:01 debconf: <-- 0 value set
Nov 17 19:37:01 debconf: SUBST passwd/user-password-crypted ID passwd/user-password-crypted
Nov 17 19:37:01 debconf: Adding [ID] -> [passwd/user-password-crypted]
Nov 17 19:37:01 debconf: <-- 0
Nov 17 19:37:01 debconf: FSET passwd/user-password-crypted seen true
Nov 17 19:37:01 debconf: <-- 0 true
```

Then, a bit further down in the file:

```
Nov 17 19:43:06 debconf: GET passwd/make-user
Nov 17 19:43:06 debconf: <-- 0 true
Nov 17 19:43:06 debconf: INPUT critical passwd/user-fullname
Nov 17 19:43:06 debconf: <-- 30 question skipped
Nov 17 19:43:06 debconf: --> GO
Nov 17 19:43:06 debconf: <-- 0 ok
Nov 17 19:43:06 debconf: GET passwd/make-user
Nov 17 19:43:06 debconf: <-- 0 true
Nov 17 19:43:06 debconf: GET passwd/username
Nov 17 19:43:06 debconf: <-- 0 pvuser
Nov 17 19:43:06 debconf: INPUT critical passwd/username
Nov 17 19:43:06 debconf: <-- 30 question skipped
Nov 17 19:43:06 debconf: --> GO
Nov 17 19:43:06 debconf: <-- 0 ok
Nov 17 19:43:06 debconf: --> GET passwd/make-user
Nov 17 19:43:06 debconf: <-- 0 true
Nov 17 19:43:06 debconf: --> GET passwd/username
Nov 17 19:43:06 debconf: <-- 0 viduser
Nov 17 19:43:06 debconf: --> GET passwd/user-password-crypted
Nov 17 19:43:06 debconf: <-- 0 <hash>
Nov 17 19:43:06 debconf: --> GO
Nov 17 19:43:06 debconf: <-- 0 ok
Nov 17 19:43:06 debconf: --> GET passwd/make-user
Nov 17 19:43:06 debconf: <-- 0 true
Nov 17 19:43:06 debconf: --> GET passwd/user-password-crypted
Nov 17 19:43:06 debconf: <-- 0 <hash>
Nov 17 19:43:06 debconf: --> GO
Nov 17 19:43:06 debconf: <-- 0 ok

```

---

