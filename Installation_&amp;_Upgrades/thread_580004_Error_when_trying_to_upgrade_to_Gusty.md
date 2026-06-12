---
title: "Error when trying to upgrade to Gusty"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Yes on 2007-10-18
I installed all my pending updates, and then updated to Gusty via Update Manager.  It's busy downloading and setting up things for about half an hour, and then it gives me this error:

```
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
```

Then Update Manager exits.  Has anyone else had this problem/know how to fix it?

Thanks.

---

### Post by mattpker on 2007-10-18
Usually this means that you loast internet connection or the file is unable to download because of to manny connections.  Try restarting your computer and running Update Manager again. If this dose not work let me know, my laptop did the same thing when it lost internet conection for a few minutes. I just ran it again.

---

### Post by linuxwizard on 2007-10-18
Try removing or disable your extra repos from source list.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Yes on 2007-10-18
Thanks, I commented out all the extra repos in my sources.list file, and closed all my Firefox browsers, and it worked fine.  

I got to the point where it told me how many things will be removed, installed, and updated, as well as about how long it will take based on two download speeds.  If I were to start installing it from that point on, are there many more confirmation spots (Where something pops up and it will wait for you to answer), or could I walk away from the computer, come back 8 hours later, and have the long remove/upgrade/install process finished?

---

### Post by Pragmatik on 2007-10-18
I hope this is not a dumb question, but how does one disable extra repositories?
Thanks!

---

### Post by linuxwizard on 2007-10-18
You should be able to comment the line with # this will disable it

---

### Post by Pragmatik on 2007-10-18
Thanks! :)

---

