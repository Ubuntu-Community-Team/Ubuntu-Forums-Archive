---
title: "&quot;Failed to initialize HAL...&quot; and other update problems"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by tomservo417 on 2008-06-21
-Installed the latest update
-Now I can't get past the username and password login screen
-If I change sessions to either GNOME or GNOME Failsafe I get the "HAL" error message but I CAN get to the desktop.
-Once there the optical drive and my USB external drive won't recognize so I can't backup and reinstall.
-Also no Internet connection while in these two sessions.

I know next to zero about the command line so any help would be incredibly appreciated.

Thanks.

---

### Post by PmDematagoda on 2008-06-21
Post the output of:-
```
dpkg -C
```

What do you mean by not being able to get past the login screen? Also, if you run:-
```
sudo /etc/init.d/hal restart
```
is it able to fix some of the problems?

---

### Post by tomservo417 on 2008-06-21
> **PmDematagoda said:**
> Post the output of:-
```
dpkg -C
```

Applying my almost zero knowledge of command line use, I'm assuming this means that I get to the command line and type "dpkg -C"  and then somehow post it here.  Is this correct?

> What do you mean by not being able to get past the login screen?

Specifically:
-I turn the machine on
-It boots
-It gets me to the input screen for a username and password
-I input that information
-It takes the information and then goes no further, hanging on a blank screen.  The blank screen is colored (Ubuntu pinkish brown).

>  Also, if you run:-
```
sudo /etc/init.d/hal restart
```
is it able to fix some of the problems?

I'll give it shot later this afternoon when I'm home. Thanks for the help so far!

---

### Post by tomservo417 on 2008-06-21
> **PmDematagoda said:**
> Post the output of:-
```
dpkg -C
```

Here it is:

The following packages need to do processing triggered by other package(s).  This processing can be requested with dpkg --triggers or the configure menu option in dselect:
 libc6        GNU C Library: Shared libraries

The following packages are only half configured, probably due to problems configuring them the first time.  The configuration should be retried using dpkg --configure <package> or the configure menu option in dselect:
 samba-common       Samba common files used by both the server and the client

The following packages have been triggered, but the trigger processesing has not yet been done.  Trigger processesing can be requested using dselect dpkg --configure --pending (or dpkg --triggers-only):
 libc6       GNU C Library: Shared Libraries

---

### Post by PmDematagoda on 2008-06-22
Ok, open up a terminal(I see you know how:)), then execute:-
```
sudo dpkg --configure -a
```
you will be prompted for your password, and while entering the password you will not see it, this is a sort of safety mechanism. Post the output of executing the command here.

---

### Post by tomservo417 on 2008-06-22
> **PmDematagoda said:**
> Ok, open up a terminal(I see you know how:)), then execute:-
```
sudo dpkg --configure -a
```
you will be prompted for your password, and while entering the password you will not see it, this is a sort of safety mechanism. Post the output of executing the command here.

Here's what I'm sitting on after executing the previous instruction:

---

### Post by PmDematagoda on 2008-06-22
Unless you configured Samba yourself, you should tell it to install the package maintainer's version, however, if you have configured Samba then you may want to keep the local version currently installed.

---

### Post by tomservo417 on 2008-06-24
So I'm at a point where I've gotten back to the desktop.  Things are still a tiny bit glitchy so I'm taking this as an opportunity/excuse to back ALL my important stuff up and do a fresh intall.  Thanks for all the help, seriously.

Also, I would like to know a bit about how I got to to here and what the steps I took in the command line actually do.  Mind if I quiz?

First question, what does dpkg -C actually mean?

---

### Post by PmDematagoda on 2008-06-25
> **tomservo417 said:**
> So I'm at a point where I've gotten back to the desktop.  Things are still a tiny bit glitchy so I'm taking this as an opportunity/excuse to back ALL my important stuff up and do a fresh intall.  Thanks for all the help, seriously.

Also, I would like to know a bit about how I got to to here and what the steps I took in the command line actually do.  Mind if I quiz?

First question, what does dpkg -C actually mean?

According to the dpkg man page(which can be viewed by executing):-
```
man dpkg
```

>  Searches for packages that have been installed only partially on your  system. dpkg will suggest what to do with them to get them working.

---

