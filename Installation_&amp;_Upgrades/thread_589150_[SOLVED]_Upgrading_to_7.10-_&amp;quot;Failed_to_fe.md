---
title: "[SOLVED] Upgrading to 7.10- &amp;quot;Failed to fetch . . . returned an error code&amp;quot;"
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

### Post by kostkon on 2007-10-23
Better go to *System -> Administration -> Software Sources* and remove this repository, because it is for *Feisty* anyway.

After the upgrade, you can add again the repository for *Wine*, but of course this time the one for *Gutsy*. Just follow the [instructions from the Wine site]("http://www.winehq.org/site/download-deb"). Don't forget to add the key, because as I can see from your second error message, the last time you did not add it.

---

### Post by Mujaheiden on 2007-10-25
okay, seems to work for me!

---

### Post by variableenigma on 2007-10-25
Yup, I've got it! Thanks :)

---

### Post by kostkon on 2007-10-25
> **variableenigma said:**
> Yup, I've got it! Thanks :)

OK, good! :)

So, did you have a good upgrade?

---

