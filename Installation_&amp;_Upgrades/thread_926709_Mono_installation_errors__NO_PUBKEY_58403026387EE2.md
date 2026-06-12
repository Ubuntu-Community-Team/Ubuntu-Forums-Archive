---
title: "Mono installation errors  NO_PUBKEY 58403026387EE263"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-09-22
When I run 
 sudo apt-get update && apt-get install monodevelop

I get the following error 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I have google but no solution yet

---

### Post by Liveman on 2009-11-04
> **hoboy said:**
> When I run 
 sudo apt-get update && apt-get install monodevelop

I get the following error 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I have google but no solution yet

Are you running BETA versjon? I do and get the same problem. But not on alfa.
//Liveman

---

### Post by sisco311 on 2009-11-04
> **Liveman said:**
> Are you running BETA versjon? I do and get the same problem. But not on alfa.
//Liveman

You have to add the public key for the wine repo:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 387EE263

```

```
sudo apt-get update
```

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by directhex on 2009-11-04
> **hoboy said:**
> When I run 
 sudo apt-get update && apt-get install monodevelop

I get the following error 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I have google but no solution yet

Utterly unrelated issue with the Wine repository.

---

