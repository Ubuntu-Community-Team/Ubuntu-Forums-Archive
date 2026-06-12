---
title: "Re-install loses user"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by daoud7 on 2008-06-01
Hi,

Using the desktop HH CD I have had to re-install on a broken system twice now.:(

On both occasions I had the same problem. 

At some point during the install I am asked to select accounts to import. It correctly lists the accounts on the HDD. I check boxes for the accounts to import (all of them).

The program then completes.

Afterwards one of the user accounts has not been installed to the list of users. It is also not possible to login as that user.:confused:

The home directory of that user is present but not useable (except maybe as su).

So, 2 questions:

Is there a bug in the install program? And a work-around?

How do I restore the files for the user which now sit in limbo. Ideally I want to use the original user name (and password).

Bright solutions sought!

---

### Post by zvacet on 2008-06-01
Boot in recovery mode and type

```
adduser username
```

If that username is administrator one then after you create it 

```
adduser username admin
```

---

