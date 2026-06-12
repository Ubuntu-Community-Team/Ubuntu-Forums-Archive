---
title: "Recreate Encrypted Private Folder?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rth on 2008-10-19
I was trying to create and then use the encrypted private folder. I didn't follow any FAQ and put in the wrong password at the beginning. No errors presented themselves... Anyway, I tried to do ecrypt-private-setup --force (can't recall the exact command, but used the --force switch) to recreate it with the correct password.

I get this:
```
Unable to read salt value from user's .ecryptfsrc file; using default
ERROR: Could not add passphrase to the current keyring
```

And I can't get into it as it won't mount:
```
fopen: No such file or directory
```

I upgraded from 8.04.1 yesterday, all patched as of this morning, 64-bit.

So, the question is, how does one flush the misconfiguration and have it accept a new configuration?

---

### Post by rth on 2008-10-20
There was an update to PAM, a reboot and a new --force and now it seems to be working.

---

### Post by rth on 2008-10-21
Well, after a reboot, it stops working.
```
keyctl_search: Required key not available
```
I can recreate it, with a --force, after I move everything out of .Private that was encrypted. I tried again, same thing, after a reboot, the message above is returned when trying to mount.

Edit:
I tried this [http://ubuntuforums.org/showthread.php?p=5907673](http://ubuntuforums.org/showthread.php?p=5907673) with the deleting and it doesn't work for me.

Edit2:
Could be this bug [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631)

---

### Post by rth on 2008-10-22
Seems fixed now. Last set of updates let's me reboot and mount the encrypted Private folder.

---

