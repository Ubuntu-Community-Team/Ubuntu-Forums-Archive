---
title: "Update Manager Fails"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Jesse Brent Coats on 2010-06-08
My Update Manager fails with the following error message:

An unresolvable problem occurred while calculating the upgrade:
The package 'skype-common' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.

This has been going on for many days, so I doubt it is a transient problem.

---

### Post by Tholley on 2010-06-08
Since it is marked for removal, you might look in Synaptic Package Manager and un-install completely from there and see if that fixes the problem.

---

### Post by boonenoob on 2010-06-08
perhaps this will work:
```

sudo apt-get --purge skype-common

```
but don't do this till someone else here checks if thats the right command

---

### Post by boonenoob on 2010-06-08
i just checked, and that is not the right command. i left something out. here is the correct command:
```

sudo apt-get remove --purge skype-common

```

---

### Post by Jesse Brent Coats on 2010-06-08
> **Tholley said:**
> Since it is marked for removal, you might look in Synaptic Package Manager and un-install completely from there and see if that fixes the problem.

Thanks!  This cleared my problem!

---

### Post by staib on 2010-06-24
And mine! Thanks boonenob, much appreciated ):P

---

