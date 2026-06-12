---
title: "$HOME /.dmrc is being ignored."
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-05-18
Hello i freshly installed Ubuntu 14.04LTS and i had ntfs partiton and on partition setup during installation i mounted it to /home/ and now every time i boot with everything goes fine but nowhere my partition and HOME/.dmrc is being ignored paragraph appears!
what is the quick fix to it?

---

### Post by Elfy on 2014-05-18
You can't use ntfs partitions for /home

It doesn't support the permissions needed.

You might be able to edit fstab and comment the /home line and allow it to boot. Or reinstall if you've just installed and not do that this time.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Go as far as step 7

Then 

```
nano /etc/fstab
```

Find the line with /home in it and put # at the beginning of the line.

Ctrl+X, enter, Y to save

Then exit from the root prompt - then resume graphical boot.

---

