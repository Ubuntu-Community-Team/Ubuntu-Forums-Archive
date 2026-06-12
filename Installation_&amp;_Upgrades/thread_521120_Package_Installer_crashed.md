---
title: "Package Installer crashed"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by campioni on 2007-08-09
Hi, I recently tried to install cdemu by installing 5 packages and something went terribly wrong. One of the package installers froze and I had to reboot to get rid of it. Now every time I try to install a package or open the Synaptic Package Manager I get an error.

Error for Synaptic Package Manager:

```
E: The package cdemu-daemon needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

But when I try to reinstall the cdemu-daemon vie the package I get:

```
Could not open 'cdemu-daemon_1.0.0-1_i386.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```

I get this error with every package btw.

Please help, I just switsched to Ubuntu from Windows XP and just got my system set up nicely, now this :(

---

### Post by campioni on 2007-08-09
Solved it myself (or more accurately by combining several tips ive found for different problems)

I hope this will someday help someone else:

First I deleted all cdemu* files from **/var/lib/dpkg/info** and then the following command finally worked (it didnt before):

```
sudo dpkg --remove --force-remove-reinstreq cdemu-daemon
```

Cheers! \\:D/

---

### Post by cmlewin on 2007-08-15
this thread just saved my life... i think... we shall see but it seems to have resolved another problem i had (very similar)

---

