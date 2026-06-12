---
title: "other users can't login"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by stuque on 2012-01-21
I've just installed 11.10, and am using Gnome shell. 

Everything seems to work okay with the account I created during setup, but any account I create with the "User Accounts" tool (or with adduser/passwd at the command-line) has the same login problem: after the password is entered the screen goes black, and then returns to the login screen.

auth.log says this about the attempted logins:

"user ingroup nopasswdlogin" not met by user

I am guessing this means the system thinks that I want to login without a password, but that's not the case: I haven't set that option for any user.

Rebooting doesn't help.

Any suggestions on how to proceed?

---

### Post by stuque on 2012-01-22
Fixed it, at least for one account ... turned out that the group/owner of a number of files was set incorrectly.

---

