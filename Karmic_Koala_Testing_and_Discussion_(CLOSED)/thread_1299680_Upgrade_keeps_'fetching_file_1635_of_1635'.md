---
title: "Upgrade keeps 'fetching file 1635 of 1635'"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mathiasdm on 2009-10-24
I started the upgrade to Karmic using 'update-manager -d', and it seems to have fetched nearly all of the packages just fine. However, it's hanging at the last file (though perhaps it's already done and is having another problem).

I would prefer not to have to download 1400 MB again, so any solution avoiding that is welcome ;)

---

### Post by slakkie on 2009-10-24
Have a look in /var/log/dist-upgrade and see what goes wrong.


In any case, don't think you will download all the packages again, since all packages are downloaded in put in the cache (/var/cache/apt).

Do you know which package it is trying to download? You could download it yourself. Add a propper Karmic repo in your sources.list:

```

deb http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

```

sudo aptitude update
sudo aptitude -d install <name of package>

Then proceed with the upgrade.

---

### Post by Mathiasdm on 2009-10-24
> **slakkie said:**
> 

In any case, don't think you will download all the packages again, since all packages are downloaded in put in the cache (/var/cache/apt).

That's what I figured (I just wasn't 100% sure), so I just cancelled and tried again. It had to download an amazing 91 kiB after that.

The installer is now installing all of the packages, I'm hoping for smooth sailing :)

---

