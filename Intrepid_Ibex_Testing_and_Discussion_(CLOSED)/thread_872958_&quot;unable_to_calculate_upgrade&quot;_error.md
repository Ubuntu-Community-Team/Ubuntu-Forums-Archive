---
title: "&quot;unable to calculate upgrade&quot; error"
date: 2008-07-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by davidshere on 2008-07-28
I've been getting "unable to calculate upgrade"... I dismissed it at first because it said that it's normal if you're running a pre-release.  But it's been going on for a while now and I'm wondering if other folks are seeing this.

I have also been getting "can only do partial upgrade"... I don't remember seeing these things when I was running the pre-release version of Hardy.

I am running this on a virtual machine; I know that's a big no-no, but maybe has nothing to do with this problem.

---

### Post by tamoneya on 2008-07-28
maybe you need a dist-upgrade.  ```
sudo apt-get dist-upgrade
``` Be careful though using it.  When it prompts you to continue make sure it isnt removing tons of packages.

also apt-get clean and apt-get check never hurt anybody.

---

### Post by davidshere on 2008-07-28
I thought the graphical upgrade was doing the "dist-upgrade".  Anyway, that appears to have fixed the problem:

```
469 upgraded, 47 newly installed, 6 to remove and 2 not upgraded.
Need to get 411MB/430MB of archives.

```

See you in five hours when it's done downloading all that...

Hmm... this can't be good:

```
Err http://us.archive.ubuntu.com intrepid/main libcups2 1.3.7-9                                                            
  404 Not Found [IP: 91.189.88.45 80]

```

---

### Post by Nullack on 2008-07-28
Dont do dist upgrades there was a thread awhile back explaining why.

---

