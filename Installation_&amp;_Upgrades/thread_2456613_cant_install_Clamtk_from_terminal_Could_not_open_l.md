---
title: "cant install Clamtk from terminal *Could not open lock file are you root ?"
date: 2021-01-15
forum: Installation &amp; Upgrades
---

### Post by voxpopili on 2021-01-15
I have been able to install other apps from terminal but i cant get Clamtk to run , i get the error message below  , what am i doing wrong please ?

" Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?

---

### Post by TheFu on 2021-01-15
> are you root? 
says it all. See the error that you posted?

Installing software from any repo requires sudo access. Normal userids don't have this authority.
If you are **really** new to Unix, this is a guide and reference to help you learn the critical things you need to know: 
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

BTW, you probably have very little use for Clam or clamtk.  Linux isn't Windows.  I only use clam on my email server and a file server that is shared with Windows people.

---

