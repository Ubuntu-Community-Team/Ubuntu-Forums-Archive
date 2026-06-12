---
title: "Removed packages  still  in /etc  /usr/lib"
date: 2019-05-10
forum: Installation &amp; Upgrades
---

### Post by WDYSUN on 2019-05-10
Dear All

for some reasons I needed to try Python3.7, I added [this PPA repo](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa)), and instaled python3.7 via apt-get. Then I decided to remove the package and the ppa.

I removed the package via 
```

sudo apt-get remove --purge   python3.7  && apt-get autoremove

```

I checked with find and there was still material on my system. Some files where cashed installation files that I removed via Synaptic. But  looking for residual stuff once again I still have

```

/etc/python3.7
/usr/lib/python3.7

```

Now the question is: there is any other better apt-get command to make sure that any related file to a given installation is properly wiped out?

Best Wishes
Pierre

---

### Post by TheFu on 2019-05-10
No. I don't think so.  I would use:
```
sudo apt purge python3.7 
```

The total size of everything in /etc/ is tiny.
```
$ sudo du -sh /etc/
39M     /etc/
```

Worried about 39MB?  I checked 15 systems here, most were less than 39M in size.  After you remove the package, it is safe to remove anything left over.

Every few weeks, I run **sudo apt autoremove** followed by autoclean. Appears that I don't have OCD, guess that's good news. Thanks. ;)

---

### Post by cruzer001 on 2019-05-10
I don't see this as major either, but I have found in the pass that "Aptitude" is sometimes a better choice.

---

### Post by deadflowr on 2019-05-10
The /usr/lib files were never part of the ppa.
Those come from the python3-gdbm package.

Not sure what the deal is with the /etc files though.

---

