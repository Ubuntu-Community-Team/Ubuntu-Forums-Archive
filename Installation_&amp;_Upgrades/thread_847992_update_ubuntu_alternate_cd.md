---
title: "update ubuntu alternate cd"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by martinm(dutch) on 2008-07-03
Hi,

I want to upgrade more than four Ubuntu 7.10 computers. At this moment the upgrade (with the alternate cd) needs to download for more than 30 minutes.

Is it possible to update the ubuntu alternate cd with the most recently packages?

Thanks,

Martin

---

### Post by dominiquec on 2008-07-03
You might want to consider using an automated install, instead.  Instructions for 7.10 are here:

[https://help.ubuntu.com/7.10/installation-guide/ia64/automatic-install.html](https://help.ubuntu.com/7.10/installation-guide/ia64/automatic-install.html)


Then, you can also set up a local repository so your computers just update from the LAN.

[http://ubuntuforums.org/showthread.php?t=599479](http://ubuntuforums.org/showthread.php?t=599479)

---

### Post by martinm(dutch) on 2008-07-03
Hi Dominiquec,

Thanks for your fast and interesting answer. Only there is a problem, the several computers are not on the same network.

Martin

---

### Post by dominiquec on 2008-07-03
Hi, Martin,

Oh, I see. Another alternative would be to gather all the repositories that you get from an updated computer (found in its /var/cache/apt directory) and create a Package.gz file.

Go to the directory where you copied all these files and run the command (you might need to install dpkg-dev first):

```
dpkg-scanpackages . /dev/null > Packages
```

Then gzip the resulting Packages file so you get Packages.gz.

Burn the Packages.gz and the .deb packages into a CD.  You can now use this to update your computers.  (Similar technique can be used to update them in the future.)

More info here:

[http://ubuntuforums.org/showthread.php?t=7455](http://ubuntuforums.org/showthread.php?t=7455)

---

### Post by dominiquec on 2008-07-03
Hi, Martin,

You might want to check out the release of 8.04.1.  That should have all the patches to date.  See [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by martinm(dutch) on 2008-07-04
Thanks a lot for both solutions. Next week I'll try the first method!

---

### Post by martinm(dutch) on 2008-07-07
:) Thanks a lot, it works!!

---

