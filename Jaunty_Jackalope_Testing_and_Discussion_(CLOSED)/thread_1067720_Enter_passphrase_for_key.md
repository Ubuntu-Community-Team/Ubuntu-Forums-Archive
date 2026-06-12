---
title: "Enter passphrase for key"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-02-12
As of restarting this morning, whenever I try and do something that requires access to my ssh key, I'm prompted for the passphrase.

Doing this once wouldn't be so bad, but I do a lot of bzr+ssh:// stuff, so this is already causing me issues as my passphrase is quite secure.

Any ideas? 

Somebody in IRC already mentioned Seahorse might not be running, but it is.

---

### Post by mullens101 on 2009-02-12
As of today I had a problem where SSH would fail (as a user).  I searched and found many references to this problem from Redhat forums.  The resolution to my issue was running "unset SSH_AUTH_SOCK" which was pointing to a gnome-keyring related file, perhaps your problem is related.

---

### Post by OliW on 2009-02-12
Tried it but still no love =(

---

### Post by OliW on 2009-02-13
Magically* fixed itself today after restarting. I had a pop-up asking for the passphrase (instead of the command line) with an option to remember it. 

Something must have decoupled it from the keyring temporarily.

*May have been unset SSH_AUTH_SOCK but I can't be sure. If you get this, try that and restart =)

---

