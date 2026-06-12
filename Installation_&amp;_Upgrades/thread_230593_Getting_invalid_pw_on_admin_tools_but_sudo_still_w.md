---
title: "Getting invalid pw on admin tools but sudo still works in terminal"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by Lord Erik on 2006-08-06
I recently installed dapper drake (keeping my existing /home partition) and all went well.  After a recent package update via synaptic I can no longer access anything that requires a password for root privilages.  I just get an error saying the pw is invalid.

If using sudo in a terminal with the same password it works fine.

Any ideas?  I've searched though the forums but havent found anything helpfull.

I've tried sudo adduser me admin, and it says I'm allready an admin.

---

### Post by az on 2006-08-06
Sudo and root are two different things.  There is no root user by default.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lord Erik on 2006-08-06
ok bad use of words on my part then.  The administrative tools ask for an administrative password.  It's this pw that it keeps telling me is invalid.  I'm assuming is should be the same pw that i use to log in and for sudo as that is the only pw I've specified when installing.

---

### Post by az on 2006-08-06
> **Lord Erik said:**
> ok bad use of words on my part then.  The administrative tools ask for an administrative password.  It's this pw that it keeps telling me is invalid.  I'm assuming is should be the same pw that i use to log in and for sudo as that is the only pw I've specified when installing.

So you have only one user?

Is this a fresh install?  Were there any errors during the install?

The password is the password - there is no seperate password for the user and for sudo.

---

### Post by Lord Erik on 2006-08-07
only one user.

Initially I tried to upgrade and got errors that I couldnt resolve so I started again with a fresh instal.  The only thing that isnt "fresh" about it is that I kept my existing /home partition with all my settings.  This seems to have worked without a problem.

My password logs me into gnome, works with sudo in a terminal but does not work when accessing the admin tools that require a password.  

Note: after the initial instal the pw did work for everything as updated packages using synaptic a couple of times before I started getting pw errors.

The the dialog box asking for the pw is also a lot bigger than it use to be with a different layout (not sure if it's just a 6.06 thing)

---

### Post by Thorndeux on 2006-08-07
Lord Erik,

try updating via the terminal with aptitude or apt get. For example:
```
sudo aptitude update
```
and
```
sudo aptitude dist-upgrade
```

I had the same problem as you had and it worked for me. See [this thread]("http://ubuntuforums.org/showthread.php?t=230883") for more details.

Cheers,
Thorn

---

### Post by Lord Erik on 2006-08-10
nope, that hasn't helped.  I've updated everything and still cant use any admin tools due to pw error.

After reading some of the other suggested threads I've figured out gksudo works but gksu doesnt and it seems to be using gksu by defualt.

---

