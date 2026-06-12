---
title: "Trouble upgrading to Edgey"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by Sinkael on 2007-03-13
I tried to use the update manager to upgrade to Edgey (6.10) from Dapper the other day and it went well at first and then my computer froze up and I was forced to do a Cold boot.

The computer restarted and it appears to be running pretty well, faster I would say then before.

However when ever I update using the Updater it tells me to do a dist update, when I try to run the Dist update I get the follow error.

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

---

### Post by Sinkael on 2007-03-14
Bump

:guitar:

---

### Post by zvacet on 2007-03-14
In your source list did you change every dapper to edgy?After that 
```
sudo aptitude update 
```
```
sudo aptitude dist-upgrade  
```

---

### Post by bulldog on 2007-03-14
> **Sinkael said:**
> Bump

:guitar:

Your question was....................?

---

### Post by Sinkael on 2007-03-14
> **zvacet said:**
> In your source list did you change every dapper to edgy?After that 
```
sudo aptitude update 
```
```
sudo aptitude dist-upgrade  
```

That seems to have fixed it.

Thanks

---

