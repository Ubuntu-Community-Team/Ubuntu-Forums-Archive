---
title: "Upgrade CD can't fetch automatix"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Klarsin on 2007-10-28
Upgrade to edgy failed resolving getautomatix.com. I havent been able to open this site in my browser. Have they shut down shop, or what. The only reason I used automatix was the easy install of java and flash. But now that I know how to do that I could dispense w/ automatix. How do I get the upgrade to finish in these cases of failed fetches.

---

### Post by taurus on 2007-10-28
Why don't you remove the automatix repos in your /etc/apt/sources.list!  Then, you don't have to worry about it later.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Klarsin on 2007-10-28
> **taurus said:**
> Why don't you remove the automatix repos in your /etc/apt/sources.list!  Then, you don't have to worry about it later.

```
gksudo gedit /etc/apt/sources.list
```

They are deleted. I'll give the upgrade another try.
Thanks

---

### Post by Klarsin on 2007-10-29
Upgrade was sucessful. 
THIS QUESTION HAS BEEN RESOLVED

---

