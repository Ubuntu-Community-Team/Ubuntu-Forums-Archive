---
title: "No access to home folder after chown"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by BBBNL on 2012-09-25
Hello,

I've done a fresh install of 12.04 after having 10.04 for a while.
I've copied some files of the old home folder to an external hdd and pasted it afterwards in the new home folder.
I got problems with permissions.

I saw on the internet that I had do this with my own username: sudo chown -R username:username /home/username

After this I wasn't able to open the home folder anymore, something with 'it is no map' or something (forgot it). After reboot I couldn't login to my home folder.
At Guest account now..who can help me?
Thanks in advance.

---

### Post by BBBNL on 2012-09-25
Put home folder on root access
on guest no sudo allowed
**** **** ****
just installed, think im going to reinstall

---

### Post by drmrgd on 2012-09-25
If you've already reinstalled, no biggie.  However, I have an idea that might be more simple - albeit a bit of a stretch perhaps.  Can you post the output of the following two commands:

```
ls -n /home/<username> # Fill in your username there
```

```
getent passwd <username> # Fill in your username there
```

I'm wondering if it's a simple matter of the user name matching the home directory, but the UID is different.  If that's the case, it's a very simple fix.

---

