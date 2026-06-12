---
title: "Upgrading to 7.10- Could not download all repository indexes"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by variableenigma on 2007-10-23
I'm trying to upgrade from 7.04 to 7.10, but when it's installing I get the error message: 
"Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."
Then, listed underneath, it says: 
"Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.bz2](http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.bz2](http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)"

I have checked my network connection, and everything is fine. I have tried upgrading several times, but to no avail. 

Usually, I only get the above message, but once another window popped up after that one that said:
"An error occurred 
The following details are provided"
Below, it says:
"W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263"

How can I fix this problem and upgrade to 7.10?

---

### Post by rsambuca on 2007-10-23
You will have to remove those outside repositories from your sources.list.  You can do this by opening a terminal and entering:```
gksudo gedit /etc/apt/sources.list
```

---

