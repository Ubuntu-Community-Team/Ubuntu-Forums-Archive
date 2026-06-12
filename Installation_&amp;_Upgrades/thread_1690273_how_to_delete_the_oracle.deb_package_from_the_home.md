---
title: "how to delete the oracle.deb package from the home folder"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by sharath2k2 on 2011-02-18
i have installed alien to convert a rpm package to the .deb package.but, in my home folder the space is too low so it has asked me to free some space before proceeding any further.i have stopped the process and found out that the folder which has been already created cannot be deleted.when i try to delete it it says that i dont have any permissions.also my home folder is full and i want it to empty now.what should i do.:(

---

### Post by sikander3786 on 2011-02-18
I think it is due to root privileges as you might have used sudo with alien (which you need to). Run nautilus from Terminal under Applications > Accessories sub-menu using this command.

```
gksudo nautilus
```

Navigate to your home folder and delete the .deb. Make sure you don't delete or modify any other files accidentally or that may leave your system unstable.

---

### Post by sharath2k2 on 2011-02-18
oh thank you so much for that.i have did that and got back my free memory.
but,i want to install the sql (oracle 10g) in the ubuntu.how can i do that.i want to install it outside the home folder.the alien wants some thing in the home folder only.i want to install it in the drives.can i do that if so how? or can i install aql that takes up very less space so that i can do it in the home it self

---

