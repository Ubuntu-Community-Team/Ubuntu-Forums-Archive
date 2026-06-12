---
title: "One other thing: root user?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by hbquikcomjamesl on 2010-02-10
I remember from RH8 installation, being asked to set a password for "root." Ubuntu installation didn't ask for anything of the sort: it just asked me to give myself a user-ID and password. Does root get the same password? Does the user I set up for myself have root-equivalent privileges? Something else entirely?

---

### Post by sisco311 on 2010-02-10
> **hbquikcomjamesl said:**
> I remember from RH8 installation, being asked to set a password for "root." Ubuntu installation didn't ask for anything of the sort: it just asked me to give myself a user-ID and password. Does root get the same password? Does the user I set up for myself have root-equivalent privileges? Something else entirely?

By default, the root account password is locked. sudo, gksu & policykit allows authorized users (by default, the first user created during the installation is authorized) to run certain programs as root without having to know the root password.

[uhelp]community/RootSudo[/uhelp]

---

### Post by gmargo on 2010-02-10
> **hbquikcomjamesl said:**
> I remember from RH8 installation, being asked to set a password for "root." Ubuntu installation didn't ask for anything of the sort: it just asked me to give myself a user-ID and password. Does root get the same password? Does the user I set up for myself have root-equivalent privileges? Something else entirely?

Ubuntu creates the default user as a member of the _admin_ group.  The **/etc/sudoers** file is set up to allow anyone in the _admin_ group to use **sudo**.  The root account has it's password disabled, but there's nothing special about it. The forum rules apparently prohibit discussing how to give the root user a password, even though it's trivial.

---

### Post by mcduck on 2010-02-10
> **gmargo said:**
> The forum rules apparently prohibit discussing how to give the root user a password, even though it's trivial.
It's prohibited exactly *because* it's trivial. Anyybody not able to figure it out shouldn't be messing with root account.. ;)

Not that it would even be needed for anything, I've yet to see anybody coming up with an example of a task that couldn't be done just as easily with sudo (+ fakeroot for some special tasks).

---

### Post by hbquikcomjamesl on 2010-02-10
True. Unlike "QSECOFR" (or QSECOFR-equivalent accounts) on OS/400, which are perfectly safe for routine use so long as you know what you're doing, "root" on Linux does give one enough rope to hang oneself, and then helps you tie the knot.

---

### Post by gmargo on 2010-02-10
> **mcduck said:**
> It's prohibited exactly *because* 

It's prohibited because newbies always think they want to run as root and someone decided this policy would magically protect them.  And it probably does.:p

---

