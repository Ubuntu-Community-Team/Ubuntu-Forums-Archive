---
title: "Update notifier installed things I told it not to."
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by duns0014 on 2007-02-14
Title says it all, I unchecked boxes for things I didn't want and it installed them anyway.  Anyone else have this problem?  Oddly enough, those things are still there when I click to see which updates are available.

---

### Post by bapoumba on 2007-02-14
Hi,
which packages are you talking about ?
Are you sure they are installed ? If they still show up in update-notifier, they should not.
You can check with:
```
aptitude show <package_name>
```

---

### Post by dekalbave on 2007-02-14
Same thing happened to me.  I unchecked the new kernel and header updates, but they installed anyway.  However, they no longer show up.

---

### Post by duns0014 on 2007-02-14
> **bapoumba said:**
> Hi,
which packages are you talking about ?
Are you sure they are installed ? If they still show up in update-notifier, they should not.
You can check with:
```
aptitude show <package_name>
```

I checked, it installed them.

It was the kernel (with drivers), a couple smb things, and some libraries.  A lirc library, some firewire one, and libiec.  They all got installed.

---

### Post by bapoumba on 2007-02-15
Hi, please try :
```
sudo aptitude update
sudo aptitude dist-upgrade
```
and paste any error message you are getting.

---

### Post by duns0014 on 2007-02-15
> **bapoumba said:**
> Hi, please try :
```
sudo aptitude update
sudo aptitude dist-upgrade
```
and paste any error message you are getting.

No errors, and that icon went away.

---

### Post by duns0014 on 2007-02-15
And interestingly, I had like 9 packages the update icon said I should upgrade, but aptitude upgraded three packages.  The others I know installed themselves before, when I didn't want them too.  Synaptic gave me the same results as aptitude.

---

### Post by bapoumba on 2007-02-15
Okay, do I understand correctly everything is fine now ?

---

### Post by duns0014 on 2007-02-15
Dammit, that icon's back and it wants me to upgrade more packages.  Some of them are the same as before (even though I upgraded them), others are new.  I think I'll just turn the program off and do dist upgrades myself once in a while.

---

